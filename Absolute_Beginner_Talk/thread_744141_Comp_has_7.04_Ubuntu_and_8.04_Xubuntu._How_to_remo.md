---
title: "Comp has 7.04 Ubuntu and 8.04 Xubuntu. How to remove Xubuntu"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by hanzj on 2008-04-03
Hello,
My computer had Ubuntu 7.04 Gnome intially, but to get something working, I had to try out Xubuntu 8.04 Beta install.

But now I have fixed the problem I faced and would like to remove Xubuntu completely.

When I had Xubuntu 8.04 installed, I chose the "guided partitioning", wherein Xubuntu was put on a separate partition on the hard drive, without touching the Ubuntu 7.10 files. 


How do I completely remove Xubuntu 8.04 and give back all the hard drive space back to Ubuntu 7.10?

Thank you!!!!

---

### Post by bumanie on 2008-04-03
Either run gparted from your 7.10 partition with 8.04 unmounted and extend the partition of 7.10 over the 8.04 partition. Or do the same with gparted live cd. You will have to reinstall grub to 7.10 as the boot flag will be on the 8.04 partition as it was installed last. You may need to alter your /boot/grub/menu.lst and possibly fstab - not quite sure as I have never done what you are planning, so have no experience with what happens to those lists with this kind of operation. Someone else on the forum may know.

---

### Post by prismpirate on 2008-04-03
Using the Ubuntu Live CD, open partition editor by going to:

System>Administration>Partition Editor

Delete the Xubuntu Partition, but you can format it to ext3 if you want a separate partition for data. If not, using the Partition Editor, expand your current Ubuntu partition to fill up the free space.

I think that GRUB will be wiped out by now, so follow this thread:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

To reinstall GRUB.

Your done removing Xubuntu!

---

