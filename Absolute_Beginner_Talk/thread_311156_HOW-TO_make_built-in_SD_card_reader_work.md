---
title: "HOW-TO make built-in SD card reader work"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Wardo on 2006-12-02
For some time I have been trying to make my built-in SD card reader work, I have a Gateway 3550GZ laptop with Edgy installed.

I came across a thread that solved my problem so I decided to post it once again to help out.

The original post is from **leomcabral** as a reply to the problem mentioned above:[http://www.ubuntuforums.org/showthread.php?t=282179&page=2&highlight=memory+card+reader]("http://www.ubuntuforums.org/showthread.php?t=282179&page=2&highlight=memory+card+reader")

> Try this,

**$ sudo modprobe tifm_sd**

Insert your sd card to test it. If it works correctly edit /etc/modules (**sudo gedit /etc/modules**) and add in the last line (new line) **tifm_sd**

Hope it helps out!

---

