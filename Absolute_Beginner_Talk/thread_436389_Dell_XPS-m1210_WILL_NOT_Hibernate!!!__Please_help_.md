---
title: "Dell XPS-m1210 WILL NOT Hibernate!!!  Please help :("
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-07
Ok guys, driving me to the edge here.

Dell XPS-M1210 with Nvidia 7400go.

System sleeps fine.

When I enable restricted Nvidia drivers, it will not hibernate.  Screen goes black, flashes a '_' for a few times, goes black again and never writes to the HD.

If I uninstall the Nvidia drivers, it hibernates fine.

Please help, I'll try anything to have both the drivers and hibernation.  Thanks.

---

### Post by gohanssjn on 2007-05-07
Biddy-ump bump.

---

### Post by jiminycricket on 2007-05-07
Have you tried [https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend) for hibernate as well?

Also, try the link in my signature to support the Nouveau 3d nVidia driver which won't have these problems.  Since you're using a new card you'd have to install nvidia-glx-new-dev instead of nvidia-glx-dev

---

### Post by gohanssjn on 2007-05-07
OH GOD, IT'S HIBERNATING

Lets see if it wakes up though :D

---

### Post by gohanssjn on 2007-05-07
Aww, no go :(

When it comes back up, I get a black screen and nothing works.  No CTL+ALT+Backspace, no CTL+ALT+F1, nothing :(

---

### Post by chriscando on 2007-05-09
I have a m1210 too, and am in the same situation.
Im curious though, when you did have hibernate working (without nvidia drivers) was it noticibly faster to start up? And were there any issues with wireless or anything like that?

---

### Post by gohanssjn on 2007-05-09
I had long boot times and network issues until I did this:

[http://forum.notebookreview.com/showthread.php?t=119817&highlight=long+boot](http://forum.notebookreview.com/showthread.php?t=119817&highlight=long+boot)

Good luck!

---

