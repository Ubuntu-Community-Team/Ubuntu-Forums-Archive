---
title: "Moving from Fedora Core to Ubuntu / GRUB settings"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by not28 on 2006-04-17
Hi, I've been using Fedora Core for about a week and I'm not very happy with it. I'm a Linux ubernewb and I'm looking for something that's more usable for beginners, so I've decided to try Ubuntu. But before I install, I have a question about the bootloader. Since I'm dual-booting Windows XP and Fedora Core, i have to use GRUB to pick an OS when I boot. So when I install Ubuntu, will its bootloader overwrite my current settings? Will I have to change anything in order to easily switch between booting Windows XP and Ubuntu. I had to do some tweaking with Fedora's bootloader in order to get things running, so I'm somewhat familiar with changing settings and whatnot. But I don't want to ruin my MBR or anything like that. Any tips or advice are greatly appreciated. Thanks.

---

### Post by taurus on 2006-04-17
Don't have to do anything except to tell the installer to install GRUB on MBR (master boot record).  It should pick up your Windows but if it's not, shouldn't be too hard to add an entry for your Windows.

---

### Post by not28 on 2006-04-17
Okay, thanks. I'll probably install it before the end of the week (no CD-Rs on hand right now) so if anything else comes up you can bet I'll be back here.

---

### Post by Qrk on 2006-04-17
Ubuntu should automatically configure Grub for you, erasing what was there before. However, Fedora should have also done this, so there is always a chance it won't work. To ease your fears, I have had Fedora configure Grub wrong, but Ubuntu hasn't made any mistakes yet. 

If you wan't to keep Fedora, Ubuntu should also add an entry for it in Grub (triple boot) but sadly, Linux distros usually do a better job detecting Windows than each other. Such is life.

---

### Post by not28 on 2006-04-17
I don't have a problem with completely reformatting my Linux disk. Like I said I'm still new to the Linux world and I'm looking for a nice distro to ease into. I'm not even sure why I started out with Fedora...

---

### Post by foxxxy79 on 2007-02-18
Hey guys,

I also am about to do this as well.  I do not like Fedora Core either and from what I can tell Ubuntu is the direction I wanted to go.  Sounds like I won't have too many problems.

Glad this post is here as I was worried about how this would go.

---

