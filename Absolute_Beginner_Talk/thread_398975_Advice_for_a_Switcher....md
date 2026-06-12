---
title: "Advice for a Switcher..."
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Volsfan91 on 2007-04-01
Hi there!

I think I'm going to finally make the leap and switch to Ubuntu. But only partially, because other members of the family want to keep Windows. >_>

Anyway, my Windows installation is jacked up, and I'm going to format and reinstall one day this week. I have a 200GB hard drive, of which I will allot 120 gigs (between two or three parts.) for an NTFS partition for the XP install. I'll then partition a logical ext3 partition (correct?) using my Gparted LiveCD using the remaining HDD space.

How does all of that sound?

Secondly, I want to know something else. I want to setup my PC to show the bootloader and then autoboot to Windows XP after 10 seconds. How would I go about setting this up?

---

### Post by mac.ryan on 2007-04-01
> **Volsfan91 said:**
> I'll then partition a logical ext3 partition (correct?) using my Gparted LiveCD using the remaining HDD space. How does all of that sound?

I would recommend (but this goes with tastes), to partition like this:[LIST=1]
[*]5/10 Gb for ubuntu system (EXT3)
[*]1 Gb swap partition (SWAP)
[*]the rest as (EXT3) that you will mount as /home (how to mount partitions is a standard question of the installer)[/LIST]This way you will keep your data (/home) safer, and you could even give windows permission to read/write that partition limiting the risk to mess up with the ubuntu installation.

Also updates of the system (or recover from having totally broken ubuntu) won't threaten your data.

> Secondly, I want to know something else. I want to setup my PC to show the bootloader and then autoboot to Windows XP after 10 seconds. How would I go about setting this up?When your ubuntu will be installed, type:

```
sudo nano /boot/grub/menu.lst
```This way you will edit the "config file" of grub, when you can choose timeout and default system.

Good luck, have fun, and show the rest of your family ubuntu is better! ;)

---

### Post by plb on 2007-04-01
You shouldn't need a gparted cd. Ubuntu's livecd should be able to set all this up just fine. Just setup and install Windows and leave some unallocated space for Ubuntu.

---

### Post by Volsfan91 on 2007-04-01
Awesome. Sounds great. Thanks for the help both of you. I'm getting hyped about not having to mess with registry cleaners or spyware removers ever again.

---

### Post by mac.ryan on 2007-04-01
> **Volsfan91 said:**
> Awesome. Sounds great. Thanks for the help both of you. I'm getting hyped about not having to mess with registry cleaners or spyware removers ever again.

Our pleasure! :)

BTW: the ubuntu installation CD runs gParted as one of it's steps (this is where I meant you should choose how to partition).

---

