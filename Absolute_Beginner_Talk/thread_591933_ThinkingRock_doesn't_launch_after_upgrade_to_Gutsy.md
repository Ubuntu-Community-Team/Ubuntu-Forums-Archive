---
title: "ThinkingRock doesn't launch after upgrade to Gutsy"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by xprinceps on 2007-10-25
The post title pretty much sums it up:
I had ThinkingRock 2.0 epsilon running fine in Feisty, but after upgrading to Gutsy it won't launch. Based on someone's suggestion, I downgraded from java 6 to 5, but this didn't solve anything.
"./thinkingrock" gives me the following output:

">Log Session: Thursday, October 25, 2007 7:55:10 PM GMT-07:00
>System Info: 
  Product Version         = ThinkingRock 2.0 Epsilon
  Operating System        = Linux version 2.6.22-14-generic running on i386
  Java; VM; Vendor; Home  = 1.5.0_13; Java HotSpot(TM) Server VM 1.5.0_13-b05; Sun Microsystems Inc.; /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre
  System Locale; Encoding = en_US (thinkingrock); UTF-8
  Home Dir.; Current Dir. = /home/mherron; /home/mherron/tr-2.0.epsilon/bin
  Installation; User Dir. = java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)"

I live and die by this program, so any help would be greatly appreciated. I'm an absolute beginner, so please talk slow and don't use big words :)

---

### Post by Luke.Hoersten on 2007-10-27
This is a problem with java:
> java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.


---

### Post by sportal on 2007-10-27
I had a similar error message with Firefox and Java.

> VM did not start up properly
java_vm: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Could not read ack from child process
Plugin: Java VM process has died.
plugin: java process died due to signal 6
  a core file was generated
Could not start JavaVM!


I fixed it with the following command:

> sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/xawt/libmawt.so

I hope this helps.

---

### Post by xprinceps on 2007-10-28
sportal,
I can't tell what the command you recommended was supposed to do, but it didn't change anything for me. I still get the exact same error message. I'm sure you're right that it's a java problem; I just don't know the nature of the problem or how to fix it.

---

### Post by xprinceps on 2007-10-28
Please, if anyone has an idea...until I get this solved I am stuck using WINDOWS!!!  :mad:

---

### Post by dfcamara on 2007-11-10
I had the same problem and the fix above worked for me too. You just have to figure the correct path to 'libmawt.so' in you system. I guess it may be:

sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/xawt/libmawt.so

---

### Post by xprinceps on 2007-11-13
Again, I tried it, and there is no change.

---

### Post by eeclark on 2007-11-15
Same problem here.  Fix did not work for me. (I know it is not ThinkingRock but still...getting the same error.)
```

edward@smallville:~$ sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/xawt/libmawt.so
[sudo] password for edward:
edward@smallville:~$ frostwire 
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
/usr/lib/frostwire/runFrostwire.sh: line 125: 17212 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)


```

---

