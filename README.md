# SafeThreadDispatchSemaphore(STONLYThreadSemaphore)
use dispatch_semaphore_t for thread safety

# code
<pre><code>
  #define ST_SEMAPHORE_LOCK(semString,...) \
  [[STONLYThreadSemaphore shareInstance] semaphoreLock:semString];\
  __VA_ARGS__;\
  [[STONLYThreadSemaphore shareInstance] semaphoreUNLock:semString];
</code></pre>
# how to use
 just use: ST_SEMAPHORE_LOCK(semString, <strong>...</strong> )   
 different lock use different semString
<pre><code>
dispatch_queue_t queue = dispatch_queue_create("test", DISPATCH_QUEUE_CONCURRENT);
dispatch_group_t group = dispatch_group_create();
dispatch_group_async(group, queue, ^{
        ST_SEMAPHORE_LOCK(@"homeTest",NSLog(@"lock-homeTest1"));
    });
</code></pre>
