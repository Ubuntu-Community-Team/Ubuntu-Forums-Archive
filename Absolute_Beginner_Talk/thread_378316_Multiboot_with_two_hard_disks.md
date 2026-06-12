---
title: "Multiboot with two hard disks"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by rodrigo juarez on 2007-03-07
Hello there, this is my first bean here.
This is not my first time with linux, I've been using it from time to time, usually when I get a new hard drive with spare space, but this will be the first time I could use an another disk for it.
I've installed linux on second partitions many times and always LILO or grub did the boot setup for me.
This time I want to have my XP disk untouched (C: and D: in IDE0 as master) and have linux in the other disk (IDE0 as slave).

So I installed linux with the HDD as master and then I moved it to slave and put back the XP HDD as master. Obviously there is no way to select linux unless I boot the computer from the slave HDD.
So I was looking for a way to make XP's boot.ini to include linux in the boot menu but i thought that it would be better to use grub (since it's already there) instead.

I saw a thread with easy to follow instructions to recover a linux installation missed from boot menu ([http://ubuntuforums.org/showthread.php?t=311822)](http://ubuntuforums.org/showthread.php?t=311822)), I thought that following the steps I could install grub on the master disk... I screwed-up my linux install. I think this was because I originally installed linux with the disk drive as master and then I change it to slave.

My problem here is that everytime I've messed up windows I have to reformat the partition and since I'm not too good at bootloaders usually the linux partition dies too. That's the reason to have linux in another HDD.

What I need is this: if XP dies (as it usually does) I want to be able to reformat the drive (or even change it) and reinstall grub in it again, so I can select again linux or XP.

My question is this: Given a working XP and linux installations, Is there an easy way to install grub on the first drive, so I can use its menu to load one or the other? and also, is it necesary to install linux with the HDD as slave (as it will finally be working) or i can install it as master and then move it to slave?


Thanks for your help.

[edit]Sorry, I forgot to tell you, XP is in a NTFS partition[/edit]

---

### Post by indytim on 2007-03-07
This might help as far as rebuilding your grub loader:

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

IndyTim

---

### Post by louieb on 2007-03-07
> **rodrigo juarez said:**
> My question is this: Given a working XP and linux installations, Is there an easy way to install grub on the first drive, so I can use its menu to load one or the other? and also, is it necesary to install linux with the HDD as slave (as it will finally be working) or i can install it as master and then move it to slave?

Not a problem. Please install the drives as you intend to keep them before doing the Linux install. The GRUB program is /boot/grub/stage2. When you install Linux on the the second drive, the installer will by default change the MBR of the first drive to run the GRUB program in the Linux install on the second drive.    

> ... I screwed-up my linux install. I think this was because I originally installed linux with the disk drive as master and then I change it to slave.Yea that confuses the heck out of GRUB and Linux. and so does using BIOS to switch hard drive boot order (in some cases)

Before you begin do yourself a favor and get and burn[LIST]
[*]Super Grub Disk
[*]Puppy Linux Live CD
[*]GParted Live CD[/LIST]Hope you don't need them but they sure make life a lot easier when things go wrong.

---

### Post by Gutti on 2007-03-07
If you got 2 hdd, you don't need to do anything fancy, just follow [these]("http://fedorajim.googlepages.com/dualbootlinux%26xpthesafeway...") instructions.

You can boot into either OS and neither one has any thing to do with the another. Simple, fast, easy and really works :D

---

### Post by rodrigo juarez on 2007-03-07
Thanks for your replies (so quick).

@indytim
I'm using Ubuntu's live CD but I can guess that a grub disk will boot faster, thanks for the link.

@louieb
Would it be possible to edit menu.lst to boot from the slave drive (given BIOS changes to boot from slave) just changing (hd0,0) to something like (hd1.0) instead of reinstalling linux?

@Gutti
Damn! Just what I need! I'll check it ASAP and post the results.

Thank you all!
(Windows users would kill for such quick support! :D )

---

### Post by rodrigo juarez on 2007-03-07
So here's the update.

It's all finally working flawlessly, however I had to reinstall Linux.
I installed it, as louieb recomended, with the drives in their final configuration.
I followed the instructions given in Gutti's link also. It was pretty straightforward, I only edited /boot/grub/menu.lst instead of grub.conf since I couldn't find it.

Thank you very much, I hope someday I know enough so I can help others as well.

---

### Post by louieb on 2007-03-07
> **rodrigo juarez said:**
>  I only edited /boot/grub/menu.lst instead of grub.conf since I couldn't find it.
Some distros such as Fedora use grub.conf others use menu.lst. At least most keep in the /boot/grub directory. I've seen some older book that have the file in the /etc directory.:confused:

---

