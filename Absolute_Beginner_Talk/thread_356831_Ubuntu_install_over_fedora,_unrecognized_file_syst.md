---
title: "Ubuntu install over fedora, unrecognized file system"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by ebubar on 2007-02-08
I have a dual boot system, windows XP and Fedora 6.0.  I want to wipe fedora and put on ubuntu 6.10.  I have the livedvd and simply need to install ubuntu over my fedora partition.  In GParted the partition where fedora is, is listed as an "uknown filesystem".  I have seen this problem listed with fedora 5.0 on one other forum, but no solution was offered.  How should I adjust my partition tables to get ubuntu installed and fedora wiped out?

Thanks in advance!

---

### Post by taurus on 2007-02-08
From the LiveCD, what's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ebubar on 2007-02-08
I'm not using the livecd right now, i'm actually in fedora.  I assume the results would be the same when using the livecd as well though...

If not, let me know and i'll go over to the livecd.

/sbin/fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        3550    28451115    7  HPFS/NTFS
/dev/sda3            9124        9729     4867695   db  CP/M / CTOS / ...
/dev/sda4            4025        9123    40957717+   5  Extended
/dev/sda5            4025        4037      104391   83  Linux
/dev/sda6            4038        9123    40853263+  8e  Linux LVM

Partition table entries are not in disk order

Thanks for the prompt reply.

---

### Post by taurus on 2007-02-08
So you are using the LVM.  Use Gparted from the LiveCD to convert it, /dev/sda6, to ext3 first before you click on the install icon.

---

### Post by click4851 on 2007-02-08
using the Gparted Live CD I think to make any changes to the Fedora part you have to tell Gparted what file system it is, like ext2 or ext3...etc. Then once its identified you should be able to delete the partition or change it. Correct me if I wrong but won't the Ubuntu Live CD see the various partitions you have and ask you where you want to install and format that area anyway, when it installs?

---

### Post by linux_kid on 2007-02-08
The installer should see this, but it will be easier if your format your drive before installing.  Im not too great in LVM partitioning, so its just an agreement with others.

---

### Post by ebubar on 2007-02-08
I've gone into Ubuntu with the livecd and converted /dev/sda6, to ext3.  Now, when doing the manual partition, what should I select?  I assume just choose to format this 39 GB partition.  
It also says I need one partition for "swap".  What should I do here?

Thanks

---

### Post by ebubar on 2007-02-08
Also, I had GRUB installed with fedora.  When I install will Ubuntu reinstall Grub and recognize my windows XP?  I know there will be an option to install GRUB to hd0...Should I just leave this?

Thanks again

---

### Post by taurus on 2007-02-08
How big is /dev/sda5?  Otherwise, you can use gparted to combine both /dev/sda5 & /dev/sda6 into a single partition and tell the installer to use the whole thing.  It will know to create one for / and one for swap.

---

### Post by ebubar on 2007-02-08
/media/sda5 is 102 Mb

---

### Post by taurus on 2007-02-08
Looks to me like /boot partition.  Therefore, use gparted to combine both /dev/sda5 & /dev/sda6 into one partition and tell the installer to use that partition/space.  It will handle / and swap for you automatically.

---

### Post by ebubar on 2007-02-08
So that i'm clear...

Use Gparted to delete the /dev/sda5 partition.  Then move the /dev/sda6 partition back to take this space essentially combining /dev/sda5 and /dev/sda6 into one ext3 filesystem.  Then, when I select next it will ask what to format.  I simply select /dev/sda6 (i guess as root "/") and the installer will know to create all the partitions (swap) that I need.  The installer will also know what to do with GRUB if I just install it in hd0 (the default option, i think) and windows XP and UBUNTU should be recognized right off the bat when I reboot.

Just making sure I know what I'm doing before I do it.

---

### Post by taurus on 2007-02-08
Yes.  Merge both /dev/sda5 and /dev/sda6 into one large partition.  Then tell the installer to use that partition and the installer will know how to create two:  one for / and one for swap (~512MB).  And install GRUB to MBR (hd0) and you can boot either Ubuntu or XP.  After you boot Ubuntu, edit /etc/fstab and add an entry for XP so that it will be mounted automatically each time you boot Ubuntu.

And if you need to access Ubuntu while you are in XP, then install this program from here.

[http://www.fs-driver.org](http://www.fs-driver.org)

Maybe this guide will help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ebubar on 2007-02-08
I get an error message about my /dev/sda1 partition being fat16 when starting the install.  Should I ignore this and continue with the install?

---

### Post by taurus on 2007-02-08
Which step are you on when you get that warning message?  Make sure you don't tell the installer to use that partition or your Dell recovery stuff would be gone.

---

### Post by ebubar on 2007-02-08
I clicked install and it started the process.  The error message popped up during this.  I had only selected the resized partition to be formatted.  I was certain not to select this dell recovery, or the windows xp stuff...  Should I try again and see if the same thing happens and write the exact error?

---

### Post by ebubar on 2007-02-08
If it is any help:

/media/sda1 = 63 Mb Partition 1
/media/sda3 = 5 Gb
/                  = 39 Gb  <---- I select only this one for the reformat
/media/sda2 = 27 Gb

____________________________________________________________________________
And on the Ready to Install screen:

GRUB will be installed to 


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
_______________________________________________________________________________

---

### Post by taurus on 2007-02-08
Or a screenshot if you can.

p.s.  Looks like it is using the unallocated space, /dev/sda5, on your harddrive then.

---

### Post by ebubar on 2007-02-09
Here is a screenshot.  Any insight ?  Should I just continue the install or do I need to do something else?

---

