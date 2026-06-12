---
title: "Copying an entire installation to a new hard drive"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2005-12-26
Hey, hope y'all had a merry $WINTER-DAY-OF-CHOICE!  I'm back in the city, ready to enjoy my new present, a brand spankin-new 120GB hard drive!  What I'd like to do is move my entire installation over to the new drive, and take the space that it occupies now and reallocate it to my shared FAT32 partition.  This is my first hardware installation experience, so I have no idea where to begin.  Anyone have some good advice?  Thx muchly, happy holidays-  pete

---

### Post by ubuntuuser on 2005-12-26
I did nearly the same a while ago. I didn't really know how to alter the bootloader files and so on, so I ended up doing a fresh install on the new drive (only until I had to reboot the PC, so I didn't do a complete installation) to get a working grub config. Then I booted a live cd (I use knoppix, but it's your choice) and copied all files and folders EXCEPT /boot on the new partition. It worked for me, although I was a bit nervous during the first boot ;) . You may have to alter the new /boot/grub/menu.lst to comment out the entry for your old partition. Let us know how it went.

edit: I don't know about the partitions in your PC. You probably also need to keep the new /etc/fstab

---

### Post by TeeAhr1 on 2005-12-27
Thx for the advice!  We're on hold right now, because the friggin' power cord is about half an inch too short to reach the bay!  I mean, for god's sake, people, think of the children!

Seriously, I'm pissed.  I mean, yeah, I could plug it in and just hang it off of the side, but there's a bay right there!  For the drive!  The cords that come with the case should reach the bay for the drive!  This is not rocket science!

Okay, I'm done.  I'll let you know how it goes once I get an extention.

Also, what if I simply make a new installation from scratch?  Can I (temporarily, don't ask, I've got an idea) have two installations of Ubuntu on my machine without making grub puke on itself?

---

### Post by ubuntuuser on 2005-12-28
As far as I understand the boot process it should work to have two ubuntu installs at the same time, as long as they are on different partitions.

---

