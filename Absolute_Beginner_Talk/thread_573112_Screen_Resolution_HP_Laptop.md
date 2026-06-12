---
title: "Screen Resolution HP Laptop"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by deaster2 on 2007-10-11
I got a H-P laptop with a Nvidia 7150M graphics card, and am
dual-booting (Gutsy and Vista). I have spent several hours
trying to get the screen resolution to 1024X768 and everything
I have tried has failed. When I try something, I get a message
stating "Ubuntu is running in low graphics mode" on restart.
I have read MANY posts in this forum and followed the
instructions to no avail. Any thoughts, suggestions help?

---

### Post by nonewmsgs on 2007-10-11
sudo dpkg-reconfigure xserver-xorg

and make sure 1024x768 is checked and it should be fine.  if something still doesn't work, tell me what hapens.  i haven't used a lot of gutsy but in feisty this has always stayed true for me.

---

### Post by deaster2 on 2007-10-15
> **nonewmsgs said:**
> sudo dpkg-reconfigure xserver-xorging 

and make sure 1024x768 is checked and it should be fine.  if something still doesn't work, tell me what hapens.  i haven't used a lot of gutsy but in feisty this has always stayed true for me.

Sorry for the delay in getting back to this thread.
Have been out of town performing presentations
with no internet connection.
Many thanks for the reply...
Had tried that many times to no avail. I finally blundered around and
found the solution which was to change the video card to
'Nvidia' instead of 'nv'. Now, for some reason, when Ubuntu is
booting, I get a Nvidia splash screen. Everything is working
fine, even Compiz.

---

