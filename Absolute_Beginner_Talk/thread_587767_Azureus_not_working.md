---
title: "Azureus not working"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-10-23
Hi I've recently upgraded to gusty, and well, azureus isn't working properly, I select it to load up and the processor goes briefly up but it doesn't load, no error or anything?  any ideas

---

### Post by dkruidhof on 2007-10-23
its a known bug, you just need to delete the log files.

here's one of many threads that talk about it:
[http://ubuntuforums.org/showthread.php?t=575204](http://ubuntuforums.org/showthread.php?t=575204)

---

### Post by Tecumseh-nl on 2007-10-23
From launchpad bug report:

> 
After reading this ([https://wiki.ubuntu.com/Bugs/HowToTriage](https://wiki.ubuntu.com/Bugs/HowToTriage)), bugs should be marked duplicate if they have the same root cause, even if they have different symptoms.

If azureus doesn't crash after the fix for bug 57875 is committed on a feisty system with the azureus in feisty-proposed and xorg+sun-java5 or xorg+sun-java6, then this bug is a duplicate. Even if they crash at different times (splash screen or sliding alert message).

What I need is for everyone with a feisty system to install the azureus package in the feisty-proposed repository or from this link:
[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)


Just removing the log files doesn't work for all configurations, like mine for instance. This proposed package does work however.

---

### Post by tony.morse on 2007-10-23
> **dkruidhof said:**
> its a known bug, you just need to delete the log files.

here's one of many threads that talk about it:
[http://ubuntuforums.org/showthread.php?t=575204](http://ubuntuforums.org/showthread.php?t=575204)

Hmm, there are no such files?

---

### Post by bardic on 2007-10-23
I have the same problem, but I just switched to kTorrent. I'm told that ktorrent performs better than azureus, though I couldn't tell ya for sure since I've only been using Ubuntu for about 5 days.  But this is what I've been told...

Just outta curiosity, can someone confirm which performs better?

---

### Post by ravenus on 2007-10-23
This post solved the problem for me without deleting any log files:
[LINK]("http://ubuntuforums.org/showpost.php?p=3584888&postcount=18")

> **misterbeetz said:**
> Yeah, I just had this problem a couple of minutes ago on 32-bit Gutsy. Removing the log files did not work for me so I used a confirmed solution in that bug report which was to install:

azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb

I got the package from here and installing it fixed the problem:

[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1%7Eproposed1_all.deb")

- misterbeetz

---

### Post by tony.morse on 2007-10-23
nope, tried installing that, and restarted, still no sign of it working???

---

### Post by dynamethod on 2007-10-23
download and install the latest version here: [http://prdownloads.sourceforge.net/azureus/Azureus_3.0.3.4_linux.tar.bz2?download](http://prdownloads.sourceforge.net/azureus/Azureus_3.0.3.4_linux.tar.bz2?download)

the version in the repos isnt up to date anyway, i had the same problem, azureus would just crash after loading, so i installed the latest version and it works very well, alot different too, great new interface

---

### Post by tony.morse on 2007-10-24
Ok, I'm being a bit dim here, but how do install that??

---

### Post by realvz on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=529431](http://ubuntuforums.org/showthread.php?t=529431)

---

### Post by magli on 2007-10-24
Also, if you have problems with it, launch it from a terminal. That way, you may get an error telling you exactly what the problem is.

---

### Post by taavi on 2007-10-24
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb464974b, pid=16834, tid=3084237712
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]

---

### Post by realvz on 2007-10-24
reinstall java runtime from add/remove programs...

or manually (not recommended)
[http://ubuntuforums.org/showthread.php?t=332674](http://ubuntuforums.org/showthread.php?t=332674)

---

### Post by taavi on 2007-10-24
The first post in topic is about Edgy ... I have Gutsy. It makes me wonder why is this kind of essentials so unmaintained in fanciest distro in planet Earth? Makes me want to stick back to Gentoo :,(

---

### Post by realvz on 2007-10-24
did u see (not recommended)?
anyway...doing add/remove programs way is the right way

---

### Post by tony.morse on 2007-10-24
no, this thread is about gusty.  Anyway I've tried that and still no luck, I've even gone through synaptics and re-intalled all java parts, still no luck.

Anyway when I type sudo azureus this is what I get...

changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/SWT (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:62)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:102)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:203)


so I guess it's a java problem???

---

### Post by gsoundsgood on 2007-10-25
i've got the same problem on gutsy.

i just downloaded azureus from
[http://azureus.sourceforge.net/download.php]("http://azureus.sourceforge.net/download.php")

and run it from terminal. it gives the following error.

"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

same error if i start it with sudo.

but it just works fine. it even picks up the torrents from my former installation.

i'm sure there's a way to really solve the problem. until then....

---

### Post by ed-koala on 2007-10-25
I've found that Deluge is a much better torrent client for Ubuntu than Azureus.  I had the same problems with Azureus as everyone else, so I went looking for another client and found Deluge, which works faster and uses less system resources.  Give it a try, you can find it at - [http://deluge-torrent.org/downloads]("http://deluge-torrent.org/downloads")

---

### Post by jonah1980 on 2007-10-25
hi i'm also having trouble with azureus, would anyone be kind enough to build the 3.0 version for gutsy amd64 as a deb?

---

### Post by tony.morse on 2007-10-25
Ok I give up on Azureus, it's a shame as I really like it.  I'm now using Deluge and that seems to work.  I'll post here again soon and let you know if my subjective experience thinks it's slower or not...

---

### Post by jonah1980 on 2007-10-27
try the new 3.0 deb: [http://www.getdeb.net/app.php?name=Azureus](http://www.getdeb.net/app.php?name=Azureus)

---

### Post by tony.morse on 2007-10-27
Ok as a final note, Deluge does seem to be as fast as Azureus.

---

### Post by ounas on 2007-10-27
Thanks ravenus it now works with your solution

:)

---

### Post by jskasia on 2007-10-28
That seem to be my problem too,

I'm on gutsy 64bit ,

Deleting *.log solve me "Shutdown unexpected" problem

Thanks to dkruidhof.

---

### Post by jonah1980 on 2007-10-29
the 3.0 version on getdeb.net works really great, i'd recommend this for people with any trouble.

---

### Post by Parallel on 2007-11-29
> **gsoundsgood said:**
> 
"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

I managed to solve this by creating the directory $HOME/.mozilla/eclipse

---

### Post by puffyzacd on 2007-12-07
Parallel's solution worked for me, although I couldn't tell you why...

*shrug*

---

### Post by mirak63 on 2008-01-05
for me too it works, though the solution seems pretty absurd and unrelated

:confused:

---

### Post by pflanzenmoerder on 2008-01-15
Sorry to revive this old thread.
I just ran into the same problem with eclipse.
Creating mozilla/eclipse solved the problem for me.
As I am developing with eclipse (and azureus is an eclipse rcp application) the problem is quite obvious to me (but it's not that obvious to me why it happens):
Eclipse and eclipse based applications use the mozilla libs internally to render a lot of things (help pages, some xml content, ...).
I don't know why the directory doesn't get created automatically and right now I don't have the time to investigate.
I hope this is helpful for other people running into problems with eclipse or eclipse based applications.

---

### Post by jvanvolk on 2008-06-18
I am using Ubuntu Hardy 8.04.  I also have Firefox 3.0 installed, and installed the latest Azures 3.1.0.0.  The $HOME/.mozilla/eclipse directory was already created on my system; however, the permission on the eclipse directory was set to root for user and group with no permission to read, write or access for either user or group.  Given this and the information from Parallel, the error message makes perfect sense.  I used sudo to change the owner of the user and group, and Azures was able to start correctly.  Before i fixed the problem with the eclipse directory, I had also not been able to log into my Vuze account, I was receiving an SSL error saying that SSL was disabled.  Once the permissions was changed, I was able to successfully log into my vuze account.

---

