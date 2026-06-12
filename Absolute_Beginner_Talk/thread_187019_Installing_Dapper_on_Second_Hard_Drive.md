---
title: "Installing Dapper on Second Hard Drive"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by lark on 2006-06-02
Okay, I am probably stupid and missing something obvious here, but I have some questions about installing Dapper Drake on my second hard drive.

I searched, but most of the questions seem to be about dual-booting on one hard drive, and I have two.  And I'm a complete Linux newbie -- I tried the liveCD and loved it, and I'd really like to 'make the switch' to using Ubuntu as my primary OS.

My second hard drive is FAT32, with 19GB space free.  I think I'm going to just buy a new one for this, though, since I don't want to move around the 18GB of archives already on there and I'm afraid to risk them.  And partitioning scares me.

Okay, here goes!  First, can I just... install it?  Run the LiveCD and tell it which hard drive to install to while installing, and then it's good to go?  (Carefully following a print-out of the installation instructions, of course.)  

This is what I thought I could do at first, but I mentioned to a techie-type that I wanted to dual-boot with Linux, and he tried to dissuade me.  He was pretty sure that if something goes wrong, my Master Boot Record will be corrupted and I'll need to reinstall Windows and lose all my existing data and general DOOM!  Is this a possible problem with a second hard drive?  Or is his warning applicable just when dual-booting on one drive?

Thanks for any answers, and I'm sorry I'm so clueless!

---

### Post by confused57 on 2006-06-02
See if there this may be what you're looking for:

[http://ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)

---

### Post by lark on 2006-06-02
Thank you, Confused57! :)  That's exactly what I was looking for.

Edit to add, I think it's the term dual-boot, it's what confused me -- I thought it just meant 'two OSes on one hard drive' and I was afraid my computer would blow up or something if I tried it with two hard drives. (I'm teh dumb.)

---

### Post by confused57 on 2006-06-02
Glad it's what you were looking for..I remember when I first installed Ubuntu, I was fumbling and stumbling to figure things out...totally lost.

A search for "dualboot" vs "dual boot" will get totally different results, I usually just search by title; searching by all posts brings up too much information and reading through them can be rather tedious.

Good luck on your install...ask if there's anything you don't quite understand.

---

### Post by aysiu on 2006-06-02
Look, read this:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by lumpki on 2006-06-02
[QUOTE=lark]This is what I thought I could do at first, but I mentioned to a techie-type that I wanted to dual-boot with Linux, and he tried to dissuade me.  He was pretty sure that if something goes wrong, my Master Boot Record will be corrupted and I'll need to reinstall Windows and lose all my existing data and general DOOM![/QUOTE]

This "tech guy" doesn't know what he's talking about. Even if you mess up your MBR, it's easy to fix-- just boot up your Windows installation media and follow the instructions. On older versions of Windows, you can use fdisk (create boot floppy and put the fdisk utility on there). The command is 'fdisk /mbr'.

---

