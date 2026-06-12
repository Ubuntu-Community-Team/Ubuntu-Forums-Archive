---
title: "A good question"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by BigG123 on 2007-03-18
Hey I wanted to know if I have a master hard drive that currently has Windows XP on it, how can I put linux dual boot on a secondary slave drive?  I was reading some forum topics and it seems like you have problems if Ubuntu isn't installed on a master drive.  But if you didn't want to touch your windows master drive and have linux on the slave with GRUB for both windows and linux, how would you do that?  Cause I can only have one MBR right?  So wouldn't that's mess up booting in windows?    Basically I'm asking how do I install Ubuntu on the slave?

---

### Post by aysiu on 2007-03-18
I don't know where you're reading about problems, but you actually have an ideal situation.

Install Ubuntu to the slave drive and install Grub to the MBR (I believe this is the default).

Ubuntu's Grub (boot loader) will most likely (in 90% of cases) automatically add Windows to the boot menu. If not, someone on these forums can help you add Windows to the /boot/grub/menu.lst file manually.

It's not as complicated as it sounds. Read more details here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by BigG123 on 2007-03-18
> **aysiu said:**
> I don't know where you're reading about problems, but you actually have an ideal situation.

Install Ubuntu to the slave drive and install Grub to the MBR (I believe this is the default).

Ubuntu's Grub (boot loader) will most likely (in 90% of cases) automatically add Windows to the boot menu. If not, someone on these forums can help you add Windows to the /boot/grub/menu.lst file manually.

It's not as complicated as it sounds. Read more details here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Yes, but I can only have one MBR right and each hard drive has it's own MBR wouldn't that confuse something?  Or does Grub install itself on both?  (remember windows is Master).

---

### Post by Icemanyurt on 2007-03-18
It should work just fine, or at least it did for me, under Horay along time ago

However; back up and archive all important files from XP, since something bad could happen.

If something bad happens, may I recommend this type setup?  (I am sure there are better ways. but this way worked really well for me)
My current setup is a bit different, but works for me.

I have several partions setup for my own needs
Master Disk (250 gigs)
Partion1:  1 gig Fat 16
Partion2: 50 gigs Fat32 
Pation3: 190 gigs Linux
Parton4: 9 gigs swap

Slave (20gigs)- NTFS

Windoze reads the Partion1 as C:\, which it needs for an install location, despite the fact its installed on the slave.  Why its fat16, I don't know.  I must have selected the incorrect option.
Partion2 is my shared access drive, where I can easily place files to be used in both environments.
Partion3: This is where Ubuntu lives, and where I spend most of my time.
Partion4: Its what I had left after using equal numbers :)

Slave- Where Windoze 2000 lives...

---

### Post by BigG123 on 2007-03-19
Actually I think I was wrong you can have more than 1 MBR.  Grub just references it to the master Hard drive.  So when you install it it will say it has detected another Operating system on the master drive and to install GRUB.  I'm correct right?

---

### Post by Campingman on 2007-03-19
This worked fine for me also, installed Ubuntu to my secondary drive (xp on master drive), Grub installed on MBR on HDA0 (windows drive, default installation selection).  After sorting out partitions on secondary drive all installed/worked fine.  After installation grub goes by default into Windows but can be edited to go into Ubuntu by default.

---

### Post by BigG123 on 2007-03-19
So your saying that when u installed Linux on your slave drive it said Grub has detected another operating system on the master hard drive and to install th GRUB loader on it?  So can you have 1 or 2 MBR's? Doesn't Linux need it's own MBR?  And Window?

---

