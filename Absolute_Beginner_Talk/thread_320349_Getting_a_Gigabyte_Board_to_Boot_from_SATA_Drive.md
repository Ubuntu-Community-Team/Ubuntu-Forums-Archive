---
title: "Getting a Gigabyte Board to Boot from SATA Drive"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by shane.gardner on 2006-12-17
If you have a Gigabyte board, in my case GA-K8NF-9, you may have issues getting Ubuntu to boot after you complete the install if you installed to a SATA drive.  See the following post for a resolution path:

[http://www.ubuntuforums.com/showthread.php?p=1897348#post1897348](http://www.ubuntuforums.com/showthread.php?p=1897348#post1897348)

Basically, you have two problems:

1.  Your SATA drive must be in a RAID in order for your bios to see it (i.e., for it to show up as a bootable drive).  If your bios doesn't see it, GRUB (the bootloader for Linux) won't see it either so no boot!

2.  The device map for the hard disks in your boot settings might not match the ones that GRUB actually sees upon booting.  In other words, when you install Ubuntu it will make your boot settings based on what it sees at the time.  But, when you reboot, GRUB will see what is in the hard disk boot order from the bios.  For example, in my situation:

From LiveCD my device map looks like:

hd0: IDE drive 1
hd1: IDE drive 2
hd2: SATA drive 1 (this is the one that has Ubuntu and the one I want to boot)
hd3: SATA drive 2

But, GRUB might see this depending on your hard disk boot order:

hd0: IDE drive 1
hd1: SATA drive 1
hd2: IDE drive 2
hd3: SATA drive 2

There is a mismatch.  I found you cannot boot directly from the SATA drive with this motherboard.  The solution is to put /boot on an IDE drive, make it the first boot drive in the bios, make the SATA w/Ubuntu the second, install GRUB on the IDE drive and modify the menu.lst in /boot on the IDE drive to point to hd1...

See this post for more detail:

[http://www.ubuntuforums.com/showthread.php?p=1897348#post1897348](http://www.ubuntuforums.com/showthread.php?p=1897348#post1897348)

---

### Post by Ecthelion on 2006-12-17
Hi,

I've had none of these problems, maybe because I already made a /boot partition when I installed Edgy on my computer.
The problem I do have is that the startup is very slow due to the fact that there are errors to mount my sata each time. So I tries to mount during 2 minutes and then suddenly it goes and my pc starts up.
I've made [a thread for my problem.]("http://ubuntuforums.org/showthread.php?t=320348")
Maybe you know something that might help...

Or do you have the same problem?

---

### Post by shane.gardner on 2006-12-17
No mine boots up fast.... just a major pain to get it to boot!

---

