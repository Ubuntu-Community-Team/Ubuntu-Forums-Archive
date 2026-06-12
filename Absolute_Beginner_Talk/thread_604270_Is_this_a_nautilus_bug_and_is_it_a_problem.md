---
title: "Is this a nautilus bug and is it a problem?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by wallywally on 2007-11-05
I suspect that to some extent this post is a continuation of the thread I started here - [http://ubuntuforums.org/showthread.php?t=602422&highlight=wallywally](http://ubuntuforums.org/showthread.php?t=602422&highlight=wallywally) - but I have marked that as being Solved since my principle problem then, that my system had died, is no longer the case (I've formatted the HD and reinstalled everything!).

Having started again I have observed that there is a file in my Home folder called nautilus-debug-log.txt which contains the following line repeated 3,034 times:

0x8177510 2007/11/06 09:34:23.8774 (USER): debug log dumped due to signal 11

Is this normal or something I need to act on?

I can't think what I was doing at exactly 09:34:23.9774 am this morning but Firefox froze and  had to be forced to shut down at one point so it could have been that.  I have very recently installed Java as well, could that be anything to do with it?

---

### Post by SpiritIsReality on 2007-11-06
howdy
It's not normal. I've never had that happen yet.
what to do about it ? I'd keep it on the back burner for times when I wanted something
to try and solve. Unless it starts causing big problems.
/var/log may have some hints as to what happened.
trails

[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22nautilus-debug-log.txt%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22nautilus-debug-log.txt%22&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=%22nautilus-debug-log.txt%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=%22nautilus-debug-log.txt%22&btnG=Google+Search&meta=)

---

### Post by FuturePilot on 2007-11-07
> **wallywally said:**
> I suspect that to some extent this post is a continuation of the thread I started here - [http://ubuntuforums.org/showthread.php?t=602422&highlight=wallywally](http://ubuntuforums.org/showthread.php?t=602422&highlight=wallywally) - but I have marked that as being Solved since my principle problem then, that my system had died, is no longer the case (I've formatted the HD and reinstalled everything!).

Having started again I have observed that there is a file in my Home folder called nautilus-debug-log.txt which contains the following line repeated 3,034 times:

0x8177510 2007/11/06 09:34:23.8774 (USER): debug log dumped due to signal 11

Is this normal or something I need to act on?

I can't think what I was doing at exactly 09:34:23.9774 am this morning but Firefox froze and  had to be forced to shut down at one point so it could have been that.  I have very recently installed Java as well, could that be anything to do with it?
It's a known issue.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471")

---

