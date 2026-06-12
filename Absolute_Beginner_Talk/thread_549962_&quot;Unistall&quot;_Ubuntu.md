---
title: "&quot;Unistall&quot; Ubuntu?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by rbc on 2007-09-13
I need to “uninstall” Ubuntu. Don’t worry, I’m not leaving Linux. It’s just that I have it installed on a computer for work. I need to return it, so I need to get it back to its previous Windows-only condition. From reading thread [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)   I know that I first need to restore the mbr. I don’t have the XP install cd, so I was going to use fixmbr.exe, and type “mbrfix /drive 0 fixmbr /yes” in the command prompt. How do I know if drive 0 is where the mbr is? If I boot with Gparted Live, the hard drive has two Windows partitions, labeled /dev/sda1 (FAT16) 47.03MB and /dev/sda2 (NTFS) 55.84GB. Does drive 0 (Windows)=sda1 (Linux)? From there, I just have to delete the Linux partition and resize, right? Thanks in advance

---

### Post by overdrank on 2007-09-13
> **rbc said:**
> I need to “uninstall” Ubuntu. Don’t worry, I’m not leaving Linux. It’s just that I have it installed on a computer for work. I need to return it, so I need to get it back to its previous Windows-only condition. From reading thread [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)   I know that I first need to restore the mbr. I don’t have the XP install cd, so I was going to use fixmbr.exe, and type “mbrfix /drive 0 fixmbr /yes” in the command prompt. How do I know if drive 0 is where the mbr is? If I boot with Gparted Live, the hard drive has two Windows partitions, labeled /dev/sda1 (FAT16) 47.03MB and /dev/sda2 (NTFS) 55.84GB. Does drive 0 (Windows)=sda1 (Linux)? From there, I just have to delete the Linux partition and resize, right? Thanks in advance

Hi maybe this link will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good luck!

---

### Post by rbc on 2007-09-13
Yeah. I checked that link yesterday, but had another question about that method. To make a backup of the MBR, in that dd command "sudo dd if=/dev/hda of=/home/ubuntu/OLDMBR.img bs=446 count=1", (of course i'd use sda instead of hda), I should only be typing sda, not sda1, right?

---

### Post by Bothered on 2007-09-13
fixmbr fixes the master boot record for a hard disk, rather than fixing something associated with a hard disk partition. Hence sda1 (linux) is not drive 0 (Windows) - sda (linux) possibly (but not necessarily) is.

---

### Post by rbc on 2007-09-13
OK. I'll give it a shot. Thanks so much

---

