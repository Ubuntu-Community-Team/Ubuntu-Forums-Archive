---
title: "Grub/Dual Boot Problem"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by general-hand-grenade on 2007-08-02
I'm new to Linux altogether and now that I'm getting into it, I'm really enjoying it. However, I have a problem. I'm running a laptop with a Vista upgrade on the internal hard drive and Ubuntu on an external one. When Ubuntu installed it apparently put Grub on the external hard drive and now I have to have the hard drive plugged in whenever I start, regardless if I want Ubuntu or Vista to start. 

Is there some way I can move Grub to my Laptop's internal hard drive, or another such way around this, so I can boot Windows without having the external hard drive attached? I have extremely limited programming knowledge, I'm afraid. Any help is greatly appreciated.

---

### Post by Hospadar on 2007-08-02
What happens when you boot up without the hard drive plugged in, does it just boot straight to windows?

Are you trying to use GRUB to boot up windows when the drive isn't plugged in as well as booting when you are loading up linux?

If that's the case you might have to make another partition on the local hard drive, because otherwise you will overwrite the windows boot loader (ntldr) and you won't be able to load windows.

It sounds like an easy enough problem to solve depending on exactly what you want to do.

---

### Post by undertakingyou on 2007-08-02
If you want grub on the first hard drive, you can use a super grub disc to install it there, or you can use the ubuntu disk.  I think to use the ubuntu disk you do apt-get install grub.  Not sure there though.  
You should also have somewhere on the internal disk that has the boot menu.   This is normally in the /boot/grub folder.   If you don't have it on the internal hard disk then when you boot without the external drive plugged in you won't have a menu.

---

### Post by general-hand-grenade on 2007-08-02
When the hard drive is not plugged in, Grub loader starts, then says there is an error and just sits there. Nothing boots.

If there is a way to boot Windows without using Grub, that would be nice. If not, I just need a simple way to move Grub. I'll try using the Ubuntu disk and see if I can get anything from it.

---

### Post by undertakingyou on 2007-08-02
whenever I have boot problems I use a super grub disc.  It can be found here [http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)
It has a menu that is "fairly" easy to follow.  And then you need to move your menu.lst to the internal drive, that way you get your menu all the time.

---

### Post by general-hand-grenade on 2007-08-02
When you say moving menu.lst, can I just copy the boot folder (including menu.lst) and put it somewhere on my internal drive? Where would this go? And what else (if anything) would I have to do to make it work properly after that?

---

### Post by logos34 on 2007-08-02
Grub (stage1 that is) is on the MBR of your internal drive.  When you start you lappy it boots grub which looks for stage2 in /boot/grub (in your case on the linux root partitionon).  If the external drive is disconnected, you get the error.  

I would recommend restoring windows bootloader using your vista install cd, then reinstall grub on the mbr of the external drive.  Or use something like EasyBCD to edit Vista bootloader to add an entry for ubuntu so you can boot it that way.

---

### Post by general-hand-grenade on 2007-08-05
Thanks so much everybody for your help - I got it sorted out with EasyBCD and now when I want to use Ubuntu I just use the SuperGrub disk to get it started. Thanks so much!

---

