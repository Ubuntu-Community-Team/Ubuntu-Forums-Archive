---
title: "Problem With Applesmc"
date: 2007-09-25
forum: Apple Intel Users
---

### Post by czechman86 on 2007-09-25
I think I have figured out what error keeps on causing my computer to crash, even after the reinstall. Every time I have a failure that either causes me to force restart or restart in general, this error appears:

```
Sep 25 21:52:45 ubuntubook kernel: [  481.260000] applesmc: wait status failed: c != 8
```

Are there any known fixes to this? Has anyone else had to deal with it. I googled it and noticed that it is reported, but could not find any fixes.

Thanks!

---

### Post by cyberdork33 on 2007-09-25
Please add a note and mark your last thread as unsolved since it did not fix the issue.

You might try recompiling the ubuntu kernel with the latest mactel patches or upgrading to a newer kernel version.
[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)

---

### Post by phonky on 2007-10-20
I am running gutsy and still having this problem

tail /var/log/messages:

```

Oct 20 11:26:13 localhost kernel: [ 6493.468000] applesmc: wait status failed: 5 != 4
Oct 20 11:26:13 localhost kernel: [ 6493.668000] applesmc: wait status failed: c != 8
Oct 20 11:31:31 localhost kernel: [ 6811.356000] applesmc: wait status failed: 5 != 4
Oct 20 11:31:31 localhost kernel: [ 6811.556000] applesmc: wait status failed: c != 8
Oct 20 11:32:32 localhost kernel: [ 6872.204000] applesmc: wait status failed: 5 != 4
Oct 20 11:32:32 localhost kernel: [ 6872.404000] applesmc: wait status failed: c != 8
Oct 20 11:34:17 localhost kernel: [ 6977.476000] applesmc: wait status failed: 5 != 4
Oct 20 11:34:17 localhost kernel: [ 6977.676000] applesmc: wait status failed: c != 8
Oct 20 11:37:56 localhost kernel: [ 7196.288000] applesmc: wait status failed: 5 != 4
Oct 20 11:37:56 localhost kernel: [ 7196.492000] applesmc: wait status failed: c != 8


```

---

### Post by FunkyM on 2007-10-21
The applesmc error messages are not a crash problem. applesmc occasionally fails to read the sensor information and spits out this message then.

You can get rid of this using "applesmc-retry-when-accessing-keys.patch" in:
[http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.23/](http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.23/)

A couple of other patches at that place might be more related though as one contains a crasher fix for core2duo Macbook Pros.

---

### Post by lloeki on 2008-06-29
I'm using a macbook pro penryn and have those messages. stopping pommed stops the flood. 
also doing some 'cat /sys/devices/platform/applesmc*/*' gives the message too, along wiht running 'sensors'.

what's really annoying is that it gets saved to the logs and accounts for 25Mb a day...

I will try the patch now.

---

### Post by undertakingyou on 2008-06-30
Any luck with those patches?  I am wondering if that is causing an issue with both the screen saver an sometimes not going into hibernate.

Also, I am running kernel 2.6.24 not 2.6.23.  Will this cause a problem with the patch?

---

### Post by lloeki on 2008-07-08
nope.

I just blacklisted applesmc module, and gave up on sensor info and backlight.

as for sensors, I load 'coretemp' module and get at least cpu cores temperatures in sensors. for nvidia chip I use nvidia-settings on gui or nvclock on commandline.

---

