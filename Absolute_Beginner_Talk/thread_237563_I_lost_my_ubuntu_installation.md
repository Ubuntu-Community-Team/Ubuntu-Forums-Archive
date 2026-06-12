---
title: "I lost my ubuntu installation"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by gusarapez on 2006-08-16
I have 2 HDD, a first IDE drive which contains an XP installation and a SATA drive with a single NTFS partition for  data.

Using the ubuntu installer, I have created a 20 GB Ext3 partition and a 3 GB swap partition in the SATA drive and installed Ubuntu.

After reboot, the boot manager (GRUB) only indicated the possibility of booting to Ubuntu, i.e. it did not see the XP installation.

After recovering the original mbr, I now can boot into Windows, but I don't known how to configure the boot manager so that I have the choice to boot into Ubuntu.

I have tried Acronis OS selector, but the program does not see the Ubuntu installation either.


Any help would be much appreciated.

Thanks

---

### Post by zxee on 2006-08-16
Although most linux users seem to ignore it I think that smart boot manger can be easier for beginners. Check it out here: [http://btmgr.webframe.org/](http://btmgr.webframe.org/)
I don't think that you've lost you ubuntu install BTW you just are having problems getting the bootloader-in this case grub to work.
You can start up from the ubuntu cd and try the grub-install command. Before that though do fdisk -l from a shell/terminal and make sure you know how your disks and partitions are identified.
Hope that helps.

---

### Post by orb9220 on 2006-08-16
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

