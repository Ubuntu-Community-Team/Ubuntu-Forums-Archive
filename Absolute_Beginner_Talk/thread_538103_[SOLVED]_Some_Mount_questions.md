---
title: "[SOLVED] Some Mount questions"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by minhamra on 2007-08-29
When looking at the output of mount I see 

/sys on /sys type sysfs (rw,nowexec,nosuid,nodev)

where does this come from? it is not in fstab.

I would like to move the /sys directory to sda2/home/myname/newsys, I figured I could mount --bind it to that directory but now I see that there is something already there and I want to make sure I am not stepping on anything.

---

### Post by cmnorton on 2007-08-29
Here's one explanation: [http://en.wikipedia.org/wiki/Sysfs](http://en.wikipedia.org/wiki/Sysfs)

---

### Post by bogolisk on 2007-08-29
> **minhamra said:**
> When looking at the output of mount I see 

/sys on /sys type sysfs (rw,nowexec,nosuid,nodev)

where does this come from? it is not in fstab.

I would like to move the /sys directory to sda2/home/myname/newsys, I figured I could mount --bind it to that directory but now I see that there is something already there and I want to make sure I am not stepping on anything.

don't touch /sys or hell would break all over. It's a window/view mapped into kernel objects.

---

### Post by minhamra on 2007-08-30
Thank you both for your input, but since I know you can set /sys up in a separate partition on install, I don't see why I can't change its location. Basically I want to have a small OS partition and 1 big data partition with /Home and /Sys as subdirectories within that partition. Makes backup nice and easy and allows me to blow away the OS install without much impact on my apps etc.

---

### Post by schorsch on 2007-08-30
/sys is just a virtual filesystem as /proc. It is generated and populated at start time and extended at running time (when plugging in USB devices e.g.). There is no need to put it somewhere else as it will be created again at  the next start. Furthermore if you move it away from a running linux I'll bet this is the last thing you do in this session .. ;-)
And it really is not huge ....
```
/sys$ pwd
/sys
/sys$ du -ksh
0       . 
```

---

### Post by bogolisk on 2007-08-30
> **minhamra said:**
> Thank you both for your input, but since I know you can set /sys up in a separate partition on install, I don't see why I can't change its location. Basically I want to have a small OS partition and 1 big data partition with /Home and /Sys as subdirectories within that partition. Makes backup nice and easy and allows me to blow away the OS install without much impact on my apps etc.

/sys (and /proc) doesn't consume any disk-space.

---

### Post by minhamra on 2007-08-30
OK got-it, I think I was approaching this from the wrong perspective, thank you all for helping.

---

