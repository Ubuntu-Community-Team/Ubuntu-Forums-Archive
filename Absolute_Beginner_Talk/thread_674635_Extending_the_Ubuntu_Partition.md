---
title: "Extending the Ubuntu Partition?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Theros123 on 2008-01-21
I just installed ubuntu 7.10 on my Asus G1s.  The installation went flawless and even wireless worked out of the box.  However, I want to enlarge my Ubuntu installation after shrinking my Vista one.  But, Vista will only shrink around 2 gigabytes?  I have a 160 gigabyte harddrive (where only 43 gigs are being used by Vista), and Ubuntu has around 6 gigs assigned to it...  How can I 1) Shrink the Vista install by around 10 gigs, and 2) Enlarge the Unbuntu one with the new space?

I've also installed Gparted on my Unbuntu install, however I can't modify any of the partitions from it.

Thanks,
Eric Huang

---

### Post by logos34 on 2008-01-21
Defrag vista two or three times.  Run chkdsk too (i.e. error-checking).
(for more [see this]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html"))

To enlarge you linux partition you'll have to download and burn the Gparted live cd.  (Root cannot be mounted during resize.)

---

### Post by Theros123 on 2008-01-22
Okay, I'll do that.  However, I also burned a disc of Gparted Live, but I can't figure out how to start it?  Do I need to boot with it?

---

### Post by housam on 2008-01-22
> **Theros123 said:**
> Okay, I'll do that.  However, I also burned a disc of Gparted Live, but I can't figure out how to start it?  Do I need to boot with it?

Yes you'll boot from Gparted live CD. or,

Boot from Gutsy live CD , open admin. you'll find Gparted tool.

---

### Post by Born-Thirsty on 2008-01-22
The Gparted Live CD is from boot, because you do not want anything running/loaded while trying to resize your hard drive, but defrag windows first.

When defragging Windows, do it in Safe Mode and make sure the screen saver and power saving options are off, so as not to interrupt the process. Defrag twice, to make sure all the files are sorted properly.

It should work fine from there

---

### Post by Theros123 on 2008-01-24
Okay, so I managed to make those changes....but I opted to just wipe the entire harddrive clean and start over.  So now I've installed a clean version of Vista on a 20 gig partition, and a 30 gig one for Ubuntu.  Then I created a 2 gig swap partition and left the rest as a NFTS shared drive.  

Right now, I'm reinstalling all the critical drivers in Vista, but so far Vista doesn't seem to be detecting the shared partition?  Why's that?

---

### Post by Theros123 on 2008-01-24
Okay, so I'm following these steps
> Installing Ubuntu Linux

To install Ubuntu Linux, reboot the system with the Ubuntu boot CD in the drive. At the "Partition disks" screen, select "Manually edit partition table." On my systems, Ubuntu found the partitions:

    * ntfs /media/hda1
    * ext3 /media/hda2
    * swap swap
    * fat32 /media/hd4

The ntfs partition is the resized Windows partition. The ext3 partition is where you want to install Ubuntu. Make sure you set the mount point to / for this partition, set the bootable flag on, and let Ubuntu format the partition. For the FAT32 partition, specify a mount point such as /share. When the configuration settings are correct, select "Finish partitioning and write changes to disk." The installer will format the ext3 and swap partitions.

I changed the shared partition to a fat32 one and mounted it to the /share...

---

