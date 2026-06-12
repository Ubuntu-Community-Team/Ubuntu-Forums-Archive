---
title: "Problem with open arena &amp; Video card"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2007-10-28
Hiya,

So i recently installed ubuntu and i am LOVING it. I've been screwing with some programs, and i came across open arena. When i tried launching it, it said something along the lines of "VIDEO CANNOT BE DISPLAYED" (im not at home, so i cant check the exact words right this second). I presume this is an error with the drivers on my radeon 9800 256 mb video card. If you could help, that would be great.

Radeon 9800 XT 256 mb ram video card
1 GB ram
3.2 GhZ processor
Whatever motherboard comes with dell XPS (i got the computer free off a friend)

---

### Post by damotor on 2007-11-02
You have to get direct rendering to run 3d programs softly. If you don't get it from  > glxinfo | grep direct try installing the restricted drivers

---

### Post by markharding557 on 2007-11-02
> **thedrizz said:**
> Hiya,

So i recently installed ubuntu and i am LOVING it. I've been screwing with some programs, and i came across open arena. When i tried launching it, it said something along the lines of "VIDEO CANNOT BE DISPLAYED" (im not at home, so i cant check the exact words right this second). I presume this is an error with the drivers on my radeon 9800 256 mb video card. If you could help, that would be great.

Radeon 9800 XT 256 mb ram video card
1 GB ram
3.2 GhZ processor
Whatever motherboard comes with dell XPS (i got the computer free off a friend)

you need to install ATI binary x.org driver,your card is listed, you will find it in add/remove you need to enable restricted repository first.
if you have already installed the driver is it enabled?
when i've installed nvidia drivers in the past you have to issue a command to enable it

---

### Post by thedrizz on 2007-12-14
well i installed them and changed the drivers in the xorg file.

I got compiz working, dont know why this doesnt

---

