---
title: "Yet another Grub-install question"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2006-09-15
Sorry for the millionth grub question posted here, but I took a look through the forums and still can't figure out how to save my install.

I'm trying to dual boot WinXP and Ubuntu.  I'm installing from the live cd.  I have three drives; 250gb SATA (this is where Windows is installed, 250gb IDE, and 80gb SATA. 

I initially tried to put Ubuntu on an 80gb sata drive by itself.  Rebooting, it would go straight into Windows with no choice about starting Ubuntu.

Then I repartitioned the 250gb SATA (with Windows on it) and installed Ubuntu into the last 100 gigs of that.  Now when booting I get an error about "could not find operating system.  It won't boot anything.

I really don't care what drive Ubuntu lives on, as long as I get the dual boot to work.

An fdisk -l shows:
Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       15952       29812   111338482+  83  Linux
/dev/sda2              17       15951   127997887+   7  HPFS/NTFS
/dev/sda3           29813       30401     4731142+   5  Extended
/dev/sda5           29813       30401     4731111   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9328    74927128+  83  Linux
/dev/sdb2            9329        9726     3196935    f  W95 Ext'd (LBA)
/dev/sdb5            9329        9726     3196903+  82  Linux swap / Solaris

In my boot/grub, I only have one file, device.map:
(fd0)	/dev/fd0
(hd0)	/dev/hdb
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc


I've tried to run grub-install but I get an error: Could not find device for /boot: Not found or not a block device.

Sorry for the long question.  What should I try next?

Thanks

---

### Post by bulldog on 2006-09-15
Are all the drives properly recognized in the BIOS and you see them at boot-time?

It shouldn't be a problem if you put Ubuntu on your 80 GB hdd.
The only thing with the live-cd is,it's putting GRUB on the first bootdisk [where your XP is]

Did you see GRUB at all?

When you put Ubuntu at the same drive as XP be sure there is enough free space and defrag several times before you install to be sure there aren no more fragged windows files on it.
Better way is to created a different partition for Ubuntu in XP and let the space unallocated for your Ubuntu.[I saw you did] 

But it seems Ubuntu didn't install GRUB correct the first time.
Maybe it couldn't find the bootdrive with your XP
Do you have native Sata on your motherboard or are you using a PCI-card with your Sata drive attached where you have o put drivers for in XP?

---

### Post by uzd4ce on 2006-09-15
Yes, I can see all the drives in BIOS.  

When booting I've never seen GRUB at all.  It's either gone straight into Windows, or I get the could not find the operating system error.

When I installed Ubuntu onto the XP drive, I partitioned first with Partition Magic, then installed into the unallocated space.

Any advice on what I can try to fix it?

---

### Post by bulldog on 2006-09-15
Try reinstalling on your 80 GB drive.
And look carefull at the end of the install process if it installs GRUB.
Or if there's an error and it can't install.

If possible make the 80 GB the first bootdevice in your BIOS.
So it will install GRUB on the same hdd.

Windows boot is for later concerne :)

---

### Post by uzd4ce on 2006-09-15
I know I'm an idiot, but which of the drives do I want GRUB to be on?

Any idea why my manual grub-install doesn't work?

---

### Post by bulldog on 2006-09-15
Where GRUB is installed makes no difference but it should be on your first bootdisk.

When you make your 80 GB your first bootdisk it installs GRUB on the same disk so there can't be a messing up.

When you later install XP it's a simple thing to add it to your menu.lst and fstab.

Why manual installation fails depends on how you did it and why it didn't install in the first place.

I think GRUB can't find your original bootdisk,see some post back if you have native Sata or a PCI card.

---

### Post by uzd4ce on 2006-09-15
What kinds of things would cause the error "Could not find device for /boot: Not found or not a block device."  when I try to run grub-install from the terminal?

I get that error no matter which drive I try to install it to.

---

