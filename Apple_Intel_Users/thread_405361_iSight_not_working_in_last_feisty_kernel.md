---
title: "iSight not working in last feisty kernel"
date: 2007-04-09
forum: Apple Intel Users
---

### Post by Azathoth_ on 2007-04-09
I compiled linux-uvc with isight support (while isight.patch) but when i upgraded feisty beta to the last kernel, it doesn't work again with V4L2, and then it doesn't work with ekiga.
Does anyone have it ok?

---

### Post by cyberdork33 on 2007-04-09
From:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

> NOTE:  isight works out of the box on Feisty Fawn(7.04)(Tested on Feisty Beta). You will need to select V4l2 as your video driver when configuring the webcam in Ekiga.

If a kernel update broke it, then you might want to use the older kernel until a solution is found.

---

### Post by Azathoth_ on 2007-04-10
> **cyberdork33 said:**
> From:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)



If a kernel update broke it, then you might want to use the older kernel until a solution is found.

The problem would be that in Feisty Final Release, it may include this kernel, or other that doesn't work with ekiga.

---

### Post by cyberdork33 on 2007-04-10
There is probably nothing you can do about it now... should file a bug report if that is the case.

---

### Post by bsantos on 2007-04-12
It isn't working in latest kernel. It broke on update -13 and still wasn't fixed:

[https://bugs.launchpad.net/bugs/86754](https://bugs.launchpad.net/bugs/86754)

Since then someone opened a bug directly related to iSight: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638)

There are other cameras with the same issues.

Lets hope a solution is found before the launch. :)

---

