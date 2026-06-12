---
title: "how to uninstall ubuntu?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by kramer3d on 2006-07-29
I have a master harddrive with XP and a slave harddrive with ubuntu on it. I want to uninstall ubuntu and have only windows xp available when booting. 

Last time I tried to do this, i used partition magic in windows and just wiped out my slave drive but the bootloader got messed up. Is there anyway to do this safely?

---

### Post by rowanparker on 2006-07-29
You need to run the Windows installation disk and fix the MBR.
Google around for info on how.

---

### Post by Ziox on 2006-07-29
my guess would be to use the Window install cd to over write the MBR (thus GRUB)...

---

### Post by DooX on 2006-07-29
Formatting of master boot record can sometimes be dangerous especially when its a Maxtor HDD.I always unnistal Ubuntu like this.I have Windows,on other HDD also.
Put inside Ubuntu instalation CD,go to part when partiotions are gonna create,delete ext3 and swap,and create FAT32 partiotions.This is how im doing this.

---

### Post by dio525i on 2006-07-29
isn't there some kind of way to use "fdisk" under windows/ms-dos to do it?....i remember the last time i had a boot-loader problem i used a boot-disk and then typed .... "fdisk /mbr" i think? should just reformat your mater boot record....i dunno....i would use ms-dos and format the mbr then use fdisk to reform your partitions and reformat them seems safe to me

---

