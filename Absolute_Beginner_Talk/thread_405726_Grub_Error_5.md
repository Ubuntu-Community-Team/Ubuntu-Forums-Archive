---
title: "Grub Error 5?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Bigmike34 on 2007-04-10
I installed Ubuntu 7.04 beta on my external harddrive and now all i get when i turn on my laptop is GRUB error 5.  Even when the external drive isn't plugged in, and i didnt make any changes to my internal drive.  I received the laptop from my university on scholarship so I never received a Windows XP disc.  So my ubuntu installation didnt boot and now i cant even boot into XP, all i can boot into is the Feisty Live CD.  Help?

Preferably right now my main focus is just being able to use XP again on my laptop, I installed ubuntu on the external drive specifically so crap like this wouldnt happen, I don't have the time to muck around with all this right now.  I was under the impression that during the installation you would be asked if you wanted Grub installed to the MBR, which i had no intention of doing.  Another problem with 7.04 apparently.

---

### Post by igknighted on 2007-04-10
Perhaps you should reinstall grub via the live CD...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by Bigmike34 on 2007-04-10
i tried re-installing it via the first method on that page (without affecting the mbr) and no luck.  I'll try it the other way as well.

---

### Post by Bigmike34 on 2007-04-10
No luck either way, i still get 

Grub loading stage 1.5

Error 5

"Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        4863    39021885    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       28395   228082806    7  HPFS/NTFS
/dev/sdb2           28396       30158    14161297+  83  Linux
/dev/sdb3           30159       30401     1951897+  82  Linux swap / Solaris"


As you see its trying to boot from my windows partition, i just wanted things to run solely off of the external drive.  Even so all its done is prevent me from doing anything.

---

### Post by igknighted on 2007-04-10
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)

> 5 : Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.

... i hope you backed it up :(.  Can you mount any of the partitions on the disk from the live CD?

---

### Post by igknighted on 2007-04-10
> **Bigmike34 said:**
> I was under the impression that during the installation you would be asked if you wanted Grub installed to the MBR, which i had no intention of doing.  Another problem with 7.04 apparently.

It doesn't specifically ask you, you need to click on the "advanced" button on the last screen of the install to get to that option.  It is a little more obvious in edgy and the grub install location in the last screen before install commences is a link you can click to change.  In dapper there was no such option.

---

### Post by Bigmike34 on 2007-04-10
> **igknighted said:**
> [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)



... i hope you backed it up :(.  Can you mount any of the partitions on the disk from the live CD?

I didnt back up my internal hard drive because i had no intention of installing anything on it.  I can mount the partitions i installed ubuntu on as well as my internal drive and tthe ntfs partition of the external drive

---

### Post by igknighted on 2007-04-10
> **Bigmike34 said:**
> I didnt back up my internal hard drive because i had no intention of installing anything on it.  I can mount the partitions i installed ubuntu on as well as my internal drive and tthe ntfs partition of the external drive

well, I would suggest that you try to find a windows disk from someone (any XP disk should do, and I have heard 98/2000 disks work as well) and run fixmbr from the recovery console.  As long as you can mount the partitions you should be safe, I wonder why you are getting that error.

---

