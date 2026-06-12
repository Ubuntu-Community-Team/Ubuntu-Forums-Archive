---
title: "unmounting /home"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by blueoyster on 2007-02-11
i am tring to unmount my /home partition to make an image of it using partimage.
but when i sudo umount /home, it states the device is busy.

how do i unmount it then?

---

### Post by taurus on 2007-02-11
You cannot unmount /home while you are still logged in.  Therefore, try booting into recovery mode and unmount /home then.

---

### Post by ardchoille42 on 2007-02-11
I would recommend, when you have time, downloading and burning this LiveCD:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

It has lots of admin tools (including Part Image) and the current version uses the WindowMaker window manager. I keep a copy in my cd wallet so I always have it with me.

Have a look at the [screenshots]("http://www.sysresccd.org/Screenshots"), especially the bottom few.

---

