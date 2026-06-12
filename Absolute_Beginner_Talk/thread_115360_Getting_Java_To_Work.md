---
title: "Getting Java To Work"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by bkv2k on 2006-01-10
I'm trying to get Java to work on my system. I wrote a simple HelloWorld program that runs fine in the IDE I'm using. I tried to run HelloWorld.jar in a command window:

java HelloWorld

It doesn't want to execute. These messages were produced:

*****
bvines@Whitestar:~/Programming/Java/Projects/HelloWorld/dist$ java HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: HelloWorld not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
bvines@Whitestar:~/Programming/Java/Projects/HelloWorld/dist$
*****

Can anyone give me a clue as to what I'm doing wrong.

Thanks!

---

### Post by ape on 2006-01-10
You need to execute the command like this:

   java -cp ./HelloWorld.jar HelloWorld

Since you have packaged your HelloWorld.class file inside of a .jar file, you need to tell java where to look for it.

---

### Post by bkv2k on 2006-01-10
[QUOTE=ape]You need to execute the command like this:

   java -cp ./HelloWorld.jar HelloWorld

Since you have packaged your HelloWorld.class file inside of a .jar file, you need to tell java where to look for it.[/QUOTE]

Thanks for the reply.

Didn't make any difference.  Same messages.

How does Ubuntu know where to find the jvm?  I edited /etc/jvm, placing a different path in it.  That didn't make any difference.  It's still using the original path for the jvm.

---

### Post by ape on 2006-01-10
What do the contents of your .jar file look like?  (just type `jar tvf HelloWorld.jar`)  Depending on how you packaged it up, you may have to call the classname itself differently.

---

