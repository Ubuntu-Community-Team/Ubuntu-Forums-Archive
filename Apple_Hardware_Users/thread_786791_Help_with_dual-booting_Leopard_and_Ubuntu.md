---
title: "Help with dual-booting Leopard and Ubuntu"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by arras on 2008-05-08
Hi all, I've been scanning the forums and haven't seen anyone else with this error (yay me for being unique! :D )

Anyways, I've been trying to dual-boot my Macbook pro (currently running leopard) with 8.04.  I've followed the instructions here - [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) and I'm running into a problem

After install completes, I try to boot into Ubuntu and I get:
No bootable device -- insert boot disk and press any key

I can power off and boot into OSX with no trouble, so I'm not really worried about that.  I'm not really sure what I'm doing wrong here

Basic steps I've followed:
Used Bootcamp to split the drive (giving about 18gb to Ubuntu)
installed rEFIt
formatted dev/sda3 at Ext3
formatted 1gb extra as swap
(didn't get any warnings about FAT partitions)
under Advanced (right before installation) made this change: '(hd0)' to '(hd0,3)' . Click 'OK', and 'Install'. 

Any help would be appreciated

---

### Post by cyberdork33 on 2008-05-08
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by arras on 2008-05-08
ahh, many thanks...guess I'm not as unique as I originally thought (no surprise there) and I didn't search quite thoroughly enough.

---

### Post by cyberdork33 on 2008-05-08
no problem.

---

