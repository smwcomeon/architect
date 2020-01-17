## Thread
	
  * 创建方式一*
	此方法是实现Runnable，避免只能继承Thread一个类，可以变相的继承另一个类
  ```java
	 Runnable runnable = new Runnable() {
	            @Override
	            public void run() {
	                for (int i = 0; i < 20; i++) {
	                    System.out.println(Thread.currentThread().getName());
	                }
	            }
	        };
	 new Thread(runnable).start();
   ```
	
* 创建方式二*
	
  ```java
	new Thread(){
	            @Override
	            public void run() {
	                super.run();
	            }
	  }.start();
    ```
    
* 枷锁方式*

  ```java
		//创建一个锁对象
		    Object obj =new Object();
		//加锁
		 synchronized (obj){
		       if (ticket>0){
		           try {
		               Thread.sleep(100);
		                    } catch (InterruptedException e) {
		                        e.printStackTrace();
		                    }
		                }
		        System.out.println(Thread.currentThread().getName()+"第"+ticket+"张票出售中。。。。。");
		            ticket --;
		 }
     ```
     
* Lock锁*
	```text
	提供了比synchronied代码块和synchronized方法更广泛的操作
	同步代码块/同步方法具有的功能Lock都有，除此之外，更面体现面向对象
	Lock锁也称为同步锁，加锁和释放锁的方法：
		public void  lock（）：加同步锁
		public void  unlock（）：释放同步锁

	lock对象的创建方式：
		Lock lock = new ReentrantLock(); 
			lock.lock();    //加锁
			lock.unlock();  //释放锁
	通常情况下，unlock（）方法一般与try..catch..finally代块连用
	```text
