---
title: "SQL Developer"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by ~chinook~ on 2008-03-07
Well, I just tried installing SQLDEVELOPER and when I try to run it ```
Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.  

Using oracle.home=/opt/sqldeveloper
Using ide.user.dir=/home/chinook/.sqldeveloper
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5400767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb54008b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb4f6e29d]
#3 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb50508ce]
#4 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb502d067]
#5 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb502d318]
#6 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xb502d61f]
#7 [0xb5d38e9d]
#8 [0xb5d31edd]
#9 [0xb5d31edd]
#10 [0xb5d2f249]
#11 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c40d]
#12 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x6310378]
#13 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c2a0]
#14 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x363) [0x6272153]
#15 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d4a96d]
#16 [0xb5d38e9d]
#17 [0xb5d31d77]
#18 [0xb5d2f249]
#19 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c40d]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
/opt/sqldeveloper/sqldeveloper/bin/../../ide/bin/launcher.sh: line 478: 27482 Aborted                 (core dumped) ${JAVA} ${APP_VM_OPTS} ${APP_SCRIPT_USER_HOME} ${APP_ENV_VARS} -classpath ${APP_CLASSPATH} ${APP_MAIN_CLASS} ${APP_APP_OPTS}
Error: SQL Developer can't recognize the JDK version

```

I get the java error as seen on the last line. I have java 6 runtime and development installed. Any help, as always will be greatly appreciated.

---

### Post by dbbolton on 2008-03-07
Which version of the JDK do you have? Maybe SQL Developer requires a different version.

---

### Post by ~chinook~ on 2008-03-07
I tried 5 and 6.

---

### Post by Rico010 on 2008-03-18
A friend of mine had a problem like this.
The problem was that his user had limited access to some files.

Try to "sudo chown -R user:group sqldevdir"

where user- is the user who's logged on, groupd- users group and sqldevdir- sqldevelopers location.
Now try to start it.

---

