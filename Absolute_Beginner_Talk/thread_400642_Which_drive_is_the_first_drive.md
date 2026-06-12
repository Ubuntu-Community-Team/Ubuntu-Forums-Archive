---
title: "Which drive is the first drive"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by flyby4 on 2007-04-03
My system is currently XP with two drives.  C: is a NTFS SCSI drive.  The other drive (to be a unix drive) is an IDE drive.  I recieved some excellent information about how to boot from a floppy using grub.  I was advised to use the alternate Cd as grub and LILO in the Live CD automatically seeks out the first disk. So question one is: I assume the alternate CD is the server image rather than the desk top version?  The second question is the drive order just the name ie c, d, e etc or is it IDE first, SCSI second or is it the disk the BIOS boot order?

---

### Post by confused57 on 2007-04-03
You can boot the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"
this will show your current partition tables on both hard drives.

You should be able to set your IDE drive to boot before your Window's drive in bios, before you install Ubuntu...grub should then recognize your IDE drive as (hd0) and install grub to your IDE mbr.  You would then need to leave your system set up this way to boot Ubuntu or Windows from grub...if you ever needed to boot Windows independent of grub, then set your bios to boot your SATA Window's drive 1st.  If you're installing with the alternate cd, the  last step is installing grub...you can select "no" when it offers to install grub to the mbr, you're presented with another screen that you can select where to install grub.  From the results of "sudo fdisk -l", you could enter something like /dev/hda or (fd0), for floppy install.

  To be absolutely sure, you could always disconnect your SATA drive when installing Ubuntu, see this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
then all you would need to do is add an entry to boot Windows using grub

Before you install Ubuntu, you might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD can boot Windows or Ubuntu and can restore the mbr of either.

See the first link in my signature for installing with the Alternate cd...the Alternate cd will install the full desktop version, same as the live cd...just make sure you don't download the server cd or do a "Command Line" install with the Alternate cd.

---

### Post by flyby4 on 2007-04-03
Thanks confused57.  Things are slowly becoming clearer.

---

### Post by confused57 on 2007-04-03
> **flyby4 said:**
> Thanks confused57.  Things are slowly becoming clearer.

It's really pretty ease, although if your drive is a SCSI, rather than SATA, you may have difficulty booting to it with grub...you could by switching your bios hard drive boot order.
If "sudo fdisk -l" recognizes the SCSI drive, what I suggested may work for booting Windows from grub...good luck.

---

### Post by flyby4 on 2007-04-04
Thanks again.  It is a scsi drive so I will try and see what happens.

---

