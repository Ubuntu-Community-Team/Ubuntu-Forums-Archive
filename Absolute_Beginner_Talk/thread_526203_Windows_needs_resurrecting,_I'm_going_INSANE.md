---
title: "Windows needs resurrecting, I'm going INSANE"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Pas_sa on 2007-08-15
Stupid dumb everything. I don't know what happened. I fixed Ubuntu after telling my BIOS to boot the Ubuntu HDD first (making the Windows one hd1 instead of hd0 in GRUB). A few changes while running the Live CD and I was back up and running after an upgrade.

I used Ubuntu straight for a solid week again, all was good. Then I tried to boot back into Windows. I had changed its GRUB entry to match the changes. It did not boot. So I swapped the boot order back, hoping the Windows boot loader would take care of things.

It didn't boot. Turned up two menu options, both 'Windows (default)' in the menu. I tried to restore the MBR through the Windows Setup recovery mode but now it just says the boot record is stuffed.. great.

For the record, I have three partitions on my Windows drive. System, Games and Files, but after Windows stuffed itself up during install, boot.ini resides on my Games drive.

I can't even get access to my files anymore in Ubuntu. Because of my constant rebooting and screwing around, the NTFS drives now want me to boot into Windows and shut down properly (WHICH OF COURSE I CAN'T DO). I installed ntfstools or whatever and I get this when running ntfsfix:

```
andrew@andrewdesktop:~$ sudo ntfsfix /dev/sda
Mounting volume... Failed to startup volume : Invalid argument
FAILED
Attempting to correct errors... FAILED
Failed to startup volume : Invalid argument
Volume is corrupt. You should run chkdsk.
andrew@andrewdesktop:~$ 

```

Yes, sda is the device name for the drive, I've run it with super cow powers but it still didn't work so now I am at a total loss.

PLEASE, PLEASE help me get back into Windows and back into my files. I am completely desperate now..

---

### Post by Pas_sa on 2007-08-15
If this helps:

```
andrew@andrewdesktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7649    61432560    f  W95 Ext'd (LBA)
/dev/sda2   *        7650       35248   221688967+   7  HPFS/NTFS
/dev/sda3           35249       60801   205254472+   7  HPFS/NTFS
/dev/sda5               2        7649    61432528+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14344   115218148+  83  Linux
/dev/sdb2           14345       14593     2000092+  82  Linux swap / Solaris
andrew@andrewdesktop:~$ 

```

I can post my GRUB and fstab too if relevant..

---

### Post by callan79 on 2007-08-15
> **Pas_sa said:**
> For the record, I have three partitions on my Windows drive. System, Games and Files, but after Windows stuffed itself up during install, boot.ini resides on my Games drive.


Hi there,

I can't really help with the fixing of your issue as I've never used NTFS with Ubuntu (it's a sin!), however my advice is really that if you ever need to re-install, do it like this :

 - swap your hard drives around, so the 120GB is primary and 500GB is secondary
 - get your Windows and Ubuntu install disks

Then :

120GB partition like this :
 - 40GB NTFS for WIndows installation
 - 20GB ext3 for Ubuntu installation
 - 1GB for Ubuntu SWAP
 - 59GB ext3 for Ubuntu HOME

Then your 500GB, you can have 1 x 500GB or 2 x 250GB partitions for storage, but make them ext3 and use the driver from [http://www.fs-driver.org](http://www.fs-driver.org) to access the storage space in Windows.

Sorry I can't fix your immediate issues, but hope my other advice is useful.

Cheers
Callan

---

### Post by Pas_sa on 2007-08-15
> **callan79 said:**
> Hi there,

I can't really help with the fixing of your issue as I've never used NTFS with Ubuntu (it's a sin!), however my advice is really that if you ever need to re-install, do it like this :

 - swap your hard drives around, so the 120GB is primary and 500GB is secondary
 - get your Windows and Ubuntu install disks

Then :

120GB partition like this :
 - 40GB NTFS for WIndows installation
 - 20GB ext3 for Ubuntu installation
 - 1GB for Ubuntu SWAP
 - 59GB ext3 for Ubuntu HOME

Then your 500GB, you can have 1 x 500GB or 2 x 250GB partitions for storage, but make them ext3 and use the driver from [http://www.fs-driver.org](http://www.fs-driver.org) to access the storage space in Windows.

Sorry I can't fix your immediate issues, but hope my other advice is useful.

Cheers
Callan

Thanks for the tips, I'll keep that in mind. Unfortunately though, I really don't want to resort to a fresh slate and reformat.. I don't have the time or resources at the moment to set my PC up again..

---

### Post by Steve1961 on 2007-08-15
If you have a windows disc boot from it and go to the recovery console.

Once there try:

fixmbr
fixboot
bootcfg /rebuild 
chkdsk /r

In that order.

---

### Post by Hospadar on 2007-08-15
I would be willing to bet you accidentally removed the nt boot loader from your mbr (master boot record) on your windows drive (i.e. by installing grub on the windows drive's mbr.  if fixmbr doesn't get windows booting, you can plop the windows boot loader back onto the drive with the install cd and the console it will let you boot into.  google around for restoring ntldr.

If fixing the mbr for windows gets windows booting fine, but removes grub, you would then have to use the livecd to install grub on the linux drive and then boot off that drive.

You may want to unplug drives while doing these fixes so only the drive you want to affect is getting changed (i.e. unplug the linux drive while fixing the windows drive, unplug the windows drive if/when you install grub)

---

### Post by Steve1961 on 2007-08-15
If none of the previous commands work, restore ntldr from the cd.  Just boot into recovery console and type:

copy d:\i386\ntldr c:\
copy d:\i386\ntdetect.com c:\

If you don't have a windows CD go to to [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) and download the xp quick boot disk which contains a copy of ntldr

---

### Post by Pas_sa on 2007-08-15
Ah but, the Games drive still has the ntldr and ntdetect.com files on it, along with a perfectly fine boot.ini.

I did the fixboot and fixmbr while the Ubuntu drive was unplugged but that did nothing (if not worsen my situation).

---

### Post by Steve1961 on 2007-08-16
OK, either do a repair installation or reinstall windows from scratch

---

### Post by Pas_sa on 2007-08-16
> **Steve1961 said:**
> OK, either do a repair installation or reinstall windows from scratch

Err.. repair didn't work (didn't really expect it to).. you're telling me there is no way I can resurrect the Windows install?..

---

### Post by Steve1961 on 2007-08-16
There comes a time when you can either fiddle around for hours trying to find a way to make things work, or just bite the bullet and reinstall windows from scratch.  I fix windows PCs for a living and you've reached the stage where I would just reinstall if I were you.

---

### Post by LaRoza on 2007-08-16
I would reinstall the MBR with the Super Grub Disk. You will not be able to boot Ubuntu after using it, without reinstalling grub.

See my sig...

---

### Post by StooJ on 2007-08-21
Are you desperate to get back into Windows to use it again, or to access your files on the windows drive?

If a reinstall is in order, you can still rescue your files by mounting the ntfs drive from Ubuntu or a Live CD, then back your files up to another hard drive.

---

