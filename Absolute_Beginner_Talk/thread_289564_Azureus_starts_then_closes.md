---
title: "Azureus starts then closes"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by RobsterUK on 2006-10-31
Just upgraded from Dapper to Edgy, and removed then reinstalled Azureus to make sure I had the latest version.

Now when I start it, it gets as far as showing the main program window then shuts down after about 3 seconds. the terminal output is:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb043bd02, pid=6223, tid=3085088432
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid6223.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

Java version output is:
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

Any ideas?

---

### Post by frodon on 2006-10-31
It's a known bug : [https://launchpad.net/distros/ubuntu/+source/azureus/+bug/57875](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/57875)
Workaround : [http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus)

I think we'll have to wait a bit to have a non-broken azureus in the repositories.

Will see if i find the exact bug report for this error.

---

### Post by frodon on 2006-10-31
This seems to be the correct bug report : [https://launchpad.net/distros/ubuntu/+source/azureus/+bug/68020](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/68020)
And a workaround is to use java-gcj instead of sun jre1.5 : ```
sudo update-alternatives --config java
```

---

### Post by RobsterUK on 2006-10-31
I followed the workaround and its fixed. Thanks

---

### Post by uberlinux on 2006-11-04
Also just did the workaround and it's fixed.  Thanks!  I'm also testing Deluge out now and I think I might like it better.
Glad to see the forums are back up now:-D

---

### Post by dr.drake on 2006-11-14
alright, this fix worked for a while, but since yesterday it is happening again:
when I start azureus I get a pop up about it not having closed properly then it goes away. (in java gcj mode)

if I use the 'fix' to select jre1.5 again, it goes away even before the error pops up....

any ideas?

---

### Post by frodon on 2006-11-14
If you have too much issues with the azureus from the repos i strongly advice you to use the latest version from the azureus website :
[http://ubuntuforums.org/showthread.php?t=144546&highlight](http://ubuntuforums.org/showthread.php?t=144546&highlight)

---

### Post by dyrer on 2006-11-14
*         1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 why java 1.5 (second option) is not working correct and azureus crash

---

### Post by dr.drake on 2006-11-15
> **dr.drake said:**
> alright, this fix worked for a while, but since yesterday it is happening again:
when I start azureus I get a pop up about it not having closed properly then it goes away. (in java gcj mode)

if I use the 'fix' to select jre1.5 again, it goes away even before the error pops up....

any ideas?

to be more precise:

azureus opens, but shuts down as soon as I click something in it. it could be the alert window or even the title bar of the main windows. it just vanishes. or if I don't click: after 10 seconds too.

I think I need to try frodon's suggestion..

---

