---
title: "xorg.conf for Macbook5,1"
date: 2009-03-19
forum: Apple Hardware Users
---

### Post by odysseus_nz on 2009-03-19
Hi,

I'm helping work on improving Macbook5,1 support documentation in openSuse and we're having a few issues around configuring X which openSuse does its best to completely mess up.  Could someone be so kind as to post their full xorg.conf for a Macbook5,1 with working touchpad, keyboard, and composite effects in KDE4.2?  A working Twinview would be great too.

Thanks!

John.

---

### Post by cyberdork33 on 2009-03-19
> **odysseus_nz said:**
> Hi,

I'm helping work on improving Macbook5,1 support documentation in openSuse and we're having a few issues around configuring X which openSuse does its best to completely mess up.  Could someone be so kind as to post their full xorg.conf for a Macbook5,1 with working touchpad, keyboard, and composite effects in KDE4.2?  A working Twinview would be great too.

Thanks!

John.
touchpad works with a modified driver that is in the mactel-support ppa:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)
I believe this has been submitted upstream.

you do not use the xorg.conf to configure, but rather an fdi file for hal... See documentation here:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid#Trackpad](https://help.ubuntu.com/community/MacBook5-1/Intrepid#Trackpad)

the kde stuff and twinview is beyond what we usually do documentation for.

---

