---
title: "Mac Mini Black Screen Problem"
date: 2008-10-03
forum: Apple Hardware Users
---

### Post by zacinaction on 2008-10-03
I have a Core 2 Due 1.83 GHz mac mini that I just installed 8.04 on.  Everything worked fine after installing and rebooting.  The first time I had the machine on for an extended period of time, the sceen simply turned black after a while.  I was able to use ctrl-alt-F1 to switch to a virtual terminal and tried restarting X, but this had no effect - when I switched back to X, the screen was still black.  Has anyone else seen this problem?

---

### Post by Life On Mars on 2008-10-04
Looks like the same as this bug reported here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/218334]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/218334")

---

### Post by iradieh on 2008-11-13
I got this issue as well
[http://ubuntuforums.org/showthread.php?p=6168179#post6168179](http://ubuntuforums.org/showthread.php?p=6168179#post6168179)

---

### Post by Paysan on 2009-01-31
Hello,

Same problem, that I solved adding this line in xorg.conf > Device like suggested in the link below:
```
Option "FramebufferCompression" "false"
```

No more problem, with compiz activated.

---

