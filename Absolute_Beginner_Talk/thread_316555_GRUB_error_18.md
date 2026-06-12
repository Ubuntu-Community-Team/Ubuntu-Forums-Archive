---
title: "GRUB error 18"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by doc95ut on 2006-12-10
I can't solve this after much searching the forums.  I have been trying various installs of Ubuntu/Kubuntu.  All was going well - all installs completed and booted fine - until I finally settled on one (Kubuntu Dapper) and tried to do a clean install.  Install completed (I chose "erase drive" as I had on previous installs when the partitioner appeared) but on first boot I get GRUB error 18.  I keep reading that the way to solve this is make sure my master boot partition is on the first part of the drive.  That sounds logical and I can open the manual partitioner on install and then I have no idea what to do.  I am installing on an older Compaq machine (whose BIOS is equally old) and using a 160 GB hard drive.  Kubuntu will be the only OS on the machine.  I have tried the Super Grub Disk, btw, it's polite but not particularly helpful.  Can someone please help?  I'm tearing my hair out and I can ill afford it.

---

### Post by Sef on 2006-12-11
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").  This is for Ubuntu, but the same prinicpal should work for Kubuntu.

---

### Post by doc95ut on 2006-12-11
OK, I solved this by doing the install again and creating two partitions, one primary ext3 that takes up 95% of my disk and one primary swap that takes up 5% of my disk.  I clicked "commit."  When I got to the "mount" screen I didn't change anything.  Left the primary mount at "/" and the swap mount at "swap" .  The system did appear to go through a formatting process (which is not what the "restore grub" howto says, but I didn't know how NOT to format the partitions).  It boots now, so I assume this is OK?  Thank you for the quick response.

---

### Post by mozetti on 2006-12-11
I'm sure that's fine, but if you're not too far along then you probably want to have /home on a separate partition. So, you could re-install and create 3 partitions (swap, /, and /home). This way, if you ever re-install your /home partition will remain and you wont lose files & settings.

---

