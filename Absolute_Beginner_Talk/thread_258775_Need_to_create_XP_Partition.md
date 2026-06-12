---
title: "Need to create XP Partition"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by SonicChao on 2006-09-16
Agh -- I have a few apps, among other things I'm going to need XP for. I already have Ubuntu on the whole hard disk (when I installed, I wiped the hard disk and put Ubuntu on it). How do I make an XP partition?

---

### Post by Qrk on 2006-09-16
This can be difficult. when you install XP it likes to overwrite the mbr. I found a guide:



Simple but time consuming Reinstall linux. This time dont ask it to reformat your partition and just ask it to install the very bare essentials (the stuff you want is already there and it will not be deleted). Then when it installs LILO/GRUB again, it realises there is already an MBR, and overwrites it with its MBR. Now when you boot LILO gives you a menu of Linux/DOS, and choosing DOS takes you to your old MBR. 

Not so simple Takes less time, but involves a little more messing around. First copy the current MBR to a different partition. So if /hda1 has your old windows (not your new windows), execute 

dd if=/dev/hda of=/dev/hda1 count=1 

This copies first sector of /dev/hda (i.e. the MBR) into the boot record of /dev/hda1. Then edit /etc/lilo.conf (or /etc/grub.conf) and tell it that there is Windows operating system installed in /dev/hda1. If you use LILO, just execute /sbin/lilo and you are all set. If you use GRUB, you need to install it again using /sbin/grub-install. I couldn't get grub-install to work because it was asking for some /dev/root to have some BIOS drive information or somesuch thing. Any way if you can run grub-install you are all set. If not dont worry, there is always the first option.

[http://www.cs.uchicago.edu/docs/opersys/multiboot](http://www.cs.uchicago.edu/docs/opersys/multiboot)

---

### Post by SonicChao on 2006-09-16
> **Qrk said:**
> This can be difficult. when you install XP it likes to overwrite the mbr. I found a guide:



Simple but time consuming Reinstall linux. This time dont ask it to reformat your partition and just ask it to install the very bare essentials (the stuff you want is already there and it will not be deleted). Then when it installs LILO/GRUB again, it realises there is already an MBR, and overwrites it with its MBR. Now when you boot LILO gives you a menu of Linux/DOS, and choosing DOS takes you to your old MBR. 

Not so simple Takes less time, but involves a little more messing around. First copy the current MBR to a different partition. So if /hda1 has your old windows (not your new windows), execute 

dd if=/dev/hda of=/dev/hda1 count=1 

This copies first sector of /dev/hda (i.e. the MBR) into the boot record of /dev/hda1. Then edit /etc/lilo.conf (or /etc/grub.conf) and tell it that there is Windows operating system installed in /dev/hda1. If you use LILO, just execute /sbin/lilo and you are all set. If you use GRUB, you need to install it again using /sbin/grub-install. I couldn't get grub-install to work because it was asking for some /dev/root to have some BIOS drive information or somesuch thing. Any way if you can run grub-install you are all set. If not dont worry, there is always the first option.

[http://www.cs.uchicago.edu/docs/opersys/multiboot](http://www.cs.uchicago.edu/docs/opersys/multiboot)

I don't have time for that. =\ Also to redo all my settings? :(

---

### Post by bulldog on 2006-09-16
Try to free space with gparted for your XP partition.
When that is created succes fully,install windows.

Reinstalling GRUB is no problem in most cases if you have the live cd.

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

You may have to alter your fstab to make your partitions correct.

---

### Post by SonicChao on 2006-09-16
Thanks. I've gotta try that. =)

---

