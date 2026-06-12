---
title: "EasyBCD Multiboot XP/Vista/Ubuntu Problem"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by KLoWnTaZ on 2007-08-25
Problem is with a program called EasyBCD
I installed XP then Vista then Ubuntu I went to vista and installed this Easy BCD
Now I can't get Ubuntu to come up just XP and Vista.

The Program has a thing called NeoGrub Bootloader
the config screen looks like this
```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries

```
I was wondering how I might get my /boot/grub/menu.lst so I could input the values into this Neogrub and see if that works.
I have a fresh install of Desktop edition of 7.04 
Any Ideas folks would love the help :)

---

### Post by ddrichardson on 2007-08-26
Using the Live CD, mount your Ubuntu partition and copy it to wherever you want it.

---

### Post by Steve1961 on 2007-08-26
Install grub to your ubuntu root partition and then point easybcd to that.  You might also want to try the beta 1.61 version of easybcd.

[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

You don't need neogrub.

---

### Post by KLoWnTaZ on 2007-08-26
> **Steve1961 said:**
> Install grub to your ubuntu root partition and then point easybcd to that.  You might also want to try the beta 1.61 version of easybcd.

[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

You don't need neogrub.

How does one install Grub? I know that I has some kind of loader with ubuntu I thought that was grub..

I got the beta build btw thanks Steve

I also have no idea how to mount my ubuntu partion using the live cd.

---

### Post by Steve1961 on 2007-08-26
> **KLoWnTaZ said:**
> How does one install Grub? I know that I has some kind of loader with ubuntu I thought that was grub..

I got the beta build btw thanks Steve

I also have no idea how to mount my ubuntu partion using the live cd.

Boot with the live cd and identify your Ubuntu partition:

sudo fdisk -l

This should give you /dev/hda1, hda2, hda3 or whatever the partition is called

The follow instructions here [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub)

but at the setup stage enter the same details as those for your root partition - e.g. if it was /dev/hda2 (hd01), then

root (hd0,1)
setup (hd0,1)

---

