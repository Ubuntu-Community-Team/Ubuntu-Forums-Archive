---
title: "Need help with install"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by Modderation on 2006-02-16
I've used windows ONLY forever.  Never touched command lines, etc.  I downloaded Ubuntu a while ago, stuck it on a CD and tried to install it on my new 100 gig external hard drive, because I didn't want to format the main one. (40 gig) after reading that almost all Linux distributions work on externals.  I was hoping to have a dual-boot, because other people who use this computer AREN'T open to new ideas and want to stick with windows.  Installation went smoothly, but when I went to boot up, it said it couldn't find the disk.  I don't know if this was something I did or what, but I sure didn't know what to do with just a command line.  I tried restarting, but the dual-boot wasn't working (I think).  It just immediately booted Linux with no Windows boot option:confused: .  In despiration, I reinstalled Linux and then, when I restarted again, the dual-boot window was there!  Yay!  I still couldn't load Ubuntu, so I loaded up Windows and looked for a way to uninstall it.  I ended up formatting the drive and recovering the master boot record from the XP installation CD.  So now, my compter worked fine...

But no Ubuntu.  I'm thinking, because it couldn't find the drive, that mabye it wont work on an external one, but I could really use some help.  Sorry I can't remember exactly what the problem was, that might be extremely helpful.

I want to use Linux but I can't afford to cause any problems with the computer.

I could REALLY use some help, guys. [-o<

---

### Post by mustang on 2006-02-16
I'd suggest trying to install it once again and when you run into that problem, write down the exact error and post it here. Otherwise, people like me trying to troubleshoot your problem will have no idea what to do.

---

### Post by cotcot on 2006-02-17
Installing ubuntu (and other distros) on external HDD is not easy. Here is some info about it : [http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)

If you have free space on your internal HD you could install ubuntu on it but install the grub loader to a floppy (reply NO on the question if grub is top be installed to the MBR and reply /dev/fd0 on the question where to install.

Resizing partition is worth to look at. 

Floppy in is grub menu ; floppy out is your actual windows boot.

Do not forget to set your partition with windows active again (use fdisk).

---

### Post by Modderation on 2006-02-17
Thanks, guys.  I'm going to try to install it on a new partition on my main hard drive.  Any errors come up, I'll post them here.  I dunno if I'll be able to for at least this weekend, I have a LOT of work and little time for tinkering.  Thanks a lot!

---

