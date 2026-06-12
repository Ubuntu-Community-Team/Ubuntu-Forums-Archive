---
title: "Think or Swim desktop platform"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by kstump on 2007-11-16
Problem:Think or Swim is a brokerage firm who has a trading desktop for Windows that is great. They also have a version for Linux. The problem is, it won't work with UBUNTU. There are two reasons. One UBUNTU doesn't give its users root capabilities. Two UBUNTU comes with Java 1.6 which just doesn't work with the thinkorswim platform.  I've seen one thread where people have been able to remove 1.6 and replace it with 6.3. Can someone inform me of how to do this? According to the Sun web site, I have 6.3 installed, but I'm afraid this is just with Fire Fox or something. Somehow I found the following message when I tried to run a Java based program: /user/lib/jvm/java-6-sun-1.6.0.3/jre  How can I replace this with 1.5 or 6.3?

---

### Post by approaching on 2007-11-16
yes, you can log in as root. it is just generally frowned upon, you don't really need to do that. just precede whatever command with sudo. ie
sudo rm /home/user/somefile
it will ask you to enter the password for the super user then you are golden. if you are more persistant about wanting to actually log in as root, go System --> Administration --> Login Screen Setup. There is something under the security tab. you may have to restart x. but that should allow the command 'su' to let you log in as root.

you can find your java version by entering the command
java --version
and i do believe that the firefox java is somehow seperate from the systems, but i am not altogether sure about that.

---

### Post by Sims2789 on 2007-11-16
> **approaching said:**
> yes, you can log in as root. it is just generally frowned upon, you don't really need to do that. just precede whatever command with sudo. ie
sudo rm /home/user/somefile
it will ask you to enter the password for the super user then you are golden. if you are more persistant about wanting to actually log in as root, go System --> Administration --> Login Screen Setup. There is something under the security tab. you may have to restart x. but that should allow the command 'su' to let you log in as root.

you can find your java version by entering the command
java --version
and i do believe that the firefox java is somehow seperate from the systems, but i am not altogether sure about that.

If you need a sudo root file browser, do this:

<pre>sudo nautilus</pre>

I think you can put a new version of Java on in Applications -> Add/Remove.

---

### Post by Tlon on 2007-11-21
Well, nobody followed up on this, and I'm having the same problem.  To be more clear, this is the error that the console spits out when I try to run the installation script:

> No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/martin/.install4j


This is what I get when I run 'java --version'":

> java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Note: the so-called JVM cache file mentioned in the first quote isn't present on my system, as far as I can tell.  I have no idea how to define INSTALL4J_JAVA_HOME.  Any ideas?

---

### Post by Tlon on 2007-11-21
Okay, I figured it out myself.  Enter the following commands:

> sudo apt-get install sun-java6-bin sun-java6-jre
INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-6-sun/
export INSTALL4J_JAVA_HOME

Then just run the installation script and you should be good to go.

---

### Post by jessecollins on 2007-11-27
This is how I installed the thinkorswim client with no problems.

1) I made a new folder in my home folder called .thinkorswim.  (The period is in front so that it is hidden).
2) Ran the install script and pointed the install into the .thinkorswim folder in my home directory.
3) Runs perfect.

Note: I am using Java 1.7.0.

java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea Client VM (build 1.7.0-b21, mixed mode, sharing)

I hope this helps someone.  Jesse

---

### Post by Tlon on 2007-11-28
D'oh...

Jesse, have you managed to make it through an automatic update?  They just rolled one out, and I haven't been able to get the client to load since (note, I haven't ever completed the update; I only know about it because my Win box updated).  The TOS autoupdate dialogue just sits at 'Checking for new version 00' and eats up proc cycles.

---

### Post by jessecollins on 2007-11-30
> **Tlon said:**
> D'oh...

Jesse, have you managed to make it through an automatic update?  They just rolled one out, and I haven't been able to get the client to load since (note, I haven't ever completed the update; I only know about it because my Win box updated).  The TOS autoupdate dialogue just sits at 'Checking for new version 00' and eats up proc cycles.

I had that same problem until I installed the client in my home directory.  

Not sure if your issue is the same as mine but my problem was because I had to use sudo to run the install script.  So, I had read access but not write access (only root had write permissions) to the thinkorswim files/directories and it would hang trying to write the updates.  I could have changed the permissions (sudo chmod) of the thinkorswim directory but I thought it would be easier to install it in my home directory (~).

---

### Post by sourcemorph on 2007-11-30
so how is it anyway... float or swim thing??

---

### Post by munkeytrader on 2007-12-29
> **Tlon said:**
> D'oh...

Jesse, have you managed to make it through an automatic update?  They just rolled one out, and I haven't been able to get the client to load since (note, I haven't ever completed the update; I only know about it because my Win box updated).  The TOS autoupdate dialogue just sits at 'Checking for new version 00' and eats up proc cycles.

I got around this by modifying the application link in the start menu to open TOS as root.  Go to /usr/share/applications, right click on the Thinkorswim icon, scripts -> gedit-root.  Modify the "Exec" line to read:
**sudo /bin/sh "/opt/thinkorswim/thinkorswim"**

---

### Post by crunchfighter on 2008-01-02
> **munkeytrader said:**
> I got around this by modifying the application link in the start menu to open TOS as root.  Go to /usr/share/applications, right click on the Thinkorswim icon, scripts -> gedit-root.  Modify the "Exec" line to read:
**sudo /bin/sh "/opt/thinkorswim/thinkorswim"**

munkey - how exactly did you do this?  I don't follow.  Mine is hanging on the auto update as well.  I got it to run correctly once after first installing and that is it.  I tried following your directions, but I don't see the script option.  I tried editing the file in that folder with gedit as well, but it came up as blank.  (thinkorswim-0.desktop)

Here is a temporary workaround I received from their developers a few weeks ago:

"Craig,

please try this:

[http://team.thinkorswim.com:7001/usergui/usergui.jnlp](http://team.thinkorswim.com:7001/usergui/usergui.jnlp)

if you have java webstart installed (the default with java,usually)
then you would launch the file that you get from this URL. This will
download and run the client application as a java webstart application
and you may have much more luck with it.

Let me know if it works, or if it blows up. I'll try and help along
the way
if there are any bumps.

Linwood Ma
CTO

773 435 3210 Voice
773 435 3232 Fax

thinkorswim, inc.
600 West Chicago Ave., Suite 100
Chicago, IL 60610"

---

### Post by crunchfighter on 2008-01-02
> **Tlon said:**
> Okay, I figured it out myself.  Enter the following commands:



Then just run the installation script and you should be good to go.

What version of java do you show after running these?  Does it autoupdate consistently?

---

### Post by crunchfighter on 2008-01-03
Here is a solution :
[http://ubuntuforums.org/showthread.php?t=657155](http://ubuntuforums.org/showthread.php?t=657155)

---

### Post by absoluteborg on 2008-02-13
Thanks Tlon, that worked for me! :)

---

### Post by kenfeyl on 2008-04-30
Hey guys, thanks for all your earlier tips. They were enough for me to get it working in Gutsy. Now in Hardy it has broken with the following message. I've done enough searching to see that similar problems have engulfed other apps since the Hardy upgrade, but none of the things that fixed them have fixed this. Any ideas?

```
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7fc0767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7fc08b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xe3d871bd]
#3 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe414edce]
#4 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138d77]
#5 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138ef3]
#6 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xe4139136]
#7 [0xf1445008]
#8 [0xf143eb6b]
#9 [0xf143eb6b]
#10 [0xf143c236]
#11 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76daeac]
#12 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf78aaaa8]
#13 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76dacdf]
#14 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xf77387ed]
#15 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xf73f030d]
#16 [0xf1444898]
#17 [0xf143ea94]
#18 [0xf143c236]
#19 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76daeac]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7fc0767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7fc081e]
#2 /usr/lib32/libX11.so.6 [0xe3d86518]
#3 /usr/lib32/libX11.so.6(XGetVisualInfo+0x26) [0xe3d7d0a6]
#4 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe41380b9]
#5 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138303]
#6 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138fa1]
#7 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xe4139136]
#8 [0xf1445008]
#9 [0xf143eb6b]
#10 [0xf143eb6b]
#11 [0xf143c236]
#12 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76daeac]
#13 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf78aaaa8]
#14 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76dacdf]
#15 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xf77387ed]
#16 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xf73f030d]
#17 [0xf1444898]
#18 [0xf143ea94]
#19 [0xf143c236]Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7fc0767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7fc08b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xe3d871bd]
#3 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe414edce]
#4 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138d77]
#5 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138ef3]
#6 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xe4139136]
#7 [0xf1445008]
#8 [0xf143eb6b]
#9 [0xf143eb6b]
#10 [0xf143c236]
#11 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76daeac]
#12 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf78aaaa8]
#13 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76dacdf]
#14 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xf77387ed]
#15 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xf73f030d]
#16 [0xf1444898]
#17 [0xf143ea94]
#18 [0xf143c236]
#19 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76daeac]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7fc0767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7fc081e]
#2 /usr/lib32/libX11.so.6 [0xe3d86518]
#3 /usr/lib32/libX11.so.6(XGetVisualInfo+0x26) [0xe3d7d0a6]
#4 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe41380b9]
#5 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138303]
#6 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xe4138fa1]
#7 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xe4139136]
#8 [0xf1445008]
#9 [0xf143eb6b]
#10 [0xf143eb6b]
#11 [0xf143c236]
#12 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76daeac]
#13 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf78aaaa8]
#14 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so [0xf76dacdf]
#15 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xf77387ed]
#16 /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xf73f030d]
#17 [0xf1444898]
#18 [0xf143ea94]
#19 [0xf143c236]
```

---

