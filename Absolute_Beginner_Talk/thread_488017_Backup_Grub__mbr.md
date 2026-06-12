---
title: "Backup Grub / mbr?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by grim1234 on 2007-06-29
Hi, I am dual booting ubuntu and xp on one hard drive. I will reinstall xp in the next few days. 

Is it possible to backup the grub or mbr so that I can put it back easily when windows overwrites it?

Or, is it possible to tell the windows xp install not to write to the mbr?

Thanks!

---

### Post by logos34 on 2007-06-29
> **grim1234 said:**
> Hi, I am dual booting ubuntu and xp on one hard drive. I will reinstall xp in the next few days. 

Is it possible to backup the grub or mbr so that I can put it back easily when windows overwrites it?

Or, is it possible to tell the windows xp install not to write to the mbr?

Thanks!

I don't think you have a choice on the windows bootloader.  But it's easy to reinstall grub.  Just use the Ubuntu live or alternate install cd.

From the live cd:

Open a terminal and type:

sudo grub

> find /boot/grub/stage1
(enter output '(hdx,y)' in next command)
> root (hdx,y)
> setup (hdx)
> quit

From the alternate install cd:

Choose 'Rescue a broken system' from menu.  In rescue mode choose 'Reinstall Grub bootloader'

---

### Post by Bohlio on 2007-06-29
The above is what I did when i reinstalled my XP partition, It restores grub as you had it before and If i remember correctly, it worked flawlessly. Good luck, and if you have any problems post back here.

---

### Post by grim1234 on 2007-06-29
Great!

Thanks a lot guys.

:popcorn:

---

### Post by gotmonkey on 2007-06-29
> **logos34 said:**
> I don't think you have a choice on the windows bootloader.  But it's easy to reinstall grub.  Just use the Ubuntu live or alternate install cd.

From the live cd:

Open a terminal and type:

sudo grub

> find /boot/grub/stage1
(enter output '(hdx,y)' in next command)
> root (hdx,y)
> setup (hdx)
> quit

From the alternate install cd:

Choose 'Rescue a broken system' from menu.  In rescue mode choose 'Reinstall Grub bootloader'

Thanks for walk-thru on grub. My mbr got messed up when I was using a partition problem to setup a usb hdd. Not sure how or why. I used that Super Grub cd to repair grub, but after doing so every time I booted, it would run fsck on the drive stating that it has been some ridiculous amount of time since the last cleaning and claimed that my drive was ext2. The above commands seemed to fix my issue. 

Thanks

---

