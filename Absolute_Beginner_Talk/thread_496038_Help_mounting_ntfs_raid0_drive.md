---
title: "Help mounting ntfs raid0 drive"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by shinkenzu on 2007-07-08
Hey guys. I'm completely new to Ubuntu/Linux and I'm having trouble accessing my raid drive. I've tried a few different things already.

I'm running a sata NTFS raid0 configuration on an nforce motherboard and I've installed dmraid. I have ubuntu installed on a seperate IDE hard drive.

Here's my  sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table



When I try to mount the drive I get this.

$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

Thank you for any help!

---

### Post by Mac Tzu on 2007-07-10
I am in the same situation as you mate.  Asus Mobo with Silcon Image SATA RAID.  I have also post else where no answer yet will keep you udpate.

---

### Post by Mac Tzu on 2007-07-13
Ahh dude i have found a useful link 

[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/355004495831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/355004495831)

here is the guts of the forum just in case it goes down.  
"Edit: FIXED!!! See below as to my specific setup - in case it can help you. But the steps I took were:

1. Install the dmraid package from packages.ubuntu.com
2. Login as the superuser in a terminal, and run "dmraid -ay" to activate the already NTFS RAID 0 volumes.
3. Make a directory for the volume, e.g. "mkdir /mnt/raid"
4. -- This is where I was stuck -- Mount the RAID volume by, "mount -t ntfs -users,owner,ro,umask=000 /dev/mapper/sil_afaiaedfbafb1 /mnt/raid" -- DONE!

My error was trying to mount "/dev/sda" or trying to mount "/dev/mapper/sil_afaiaedfbafb" instead of the 2nd volume "sil_afaiaedfbafb1" (note the "1" at the end).

Sorry for being such a noob, but hopefully this'll help someone else as well!"
Please above fix is not mine i would like to thank Boogs for posting their fix 

GL

---

### Post by The Caped Crusader on 2007-08-23
Hello

Same problem here! I have two SAMSUNG 160Gb drives on an Nvidia RAID0 setup.

Here's what dmraid -r says:

/dev/sda: nvidia, "nvidia_chffadbb", stripe, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_chffadbb", stripe, ok, 312581806 sectors, data@ 0

On the other hand, dmraid -ay says:

/dev/sda: nvidia, "nvidia_chffadbb", stripe, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_chffadbb1", stripe, ok, 312581806 sectors, data@ 0

I wonder why there's a '1' after the second disk when i use the option -ay but not when i use the option -r...

but whenever i try to mount the raid set is doesn't comply.

---

