---
title: "Can't seem to find my drives"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by thenme on 2007-04-02
So I have just very recently moved from windows to ubuntu. I started a few days ago with a live dvd that I got out of a Linux Mag. and though it was a good move. The Distro is ubuntu Edgy Eft 6.10 
I first tried the dual boot with limited success, thats fine though screw windows.  I installed ubuntu on an older hard drive to make sure I could get it up and running. That worked out. When I said new I mean it. It took me two hours to figure out how to install  vlc media player. Not knowing what the command line or the synaptic package manager was or a repository or...... you get the point.  Anyway I wanted to start adding back in my other hard drives so I could access my saved files and I have hit a wall.

If the drives are plugged in the boot fails "grub error 17" grub error 22" I have seen both these errors using different setups.
Also when I was still in windows I formatted one of my drives to ext3, with it plugged in I got the grub error 17 but I was able to boot from hard drive 1 using the live DVD if I run sudo fdisk  /dev/hdb I get a message that says its unable to open.

I have searched for the answer but most threads lead to solutions that have not worked for me.  

My ultimate goal here is to eliminate windows all together including the ntfs file system with out losing all my files.  Any help would be great. Remember I'm a total noob. So take it easy on me. Thanks

---

### Post by mikeyphi on 2007-04-02
Hi and welcome to Ubuntu! Most of us had some problems to start with!

I think we'll need some more info to understand your system before offering advice.
But later on you could also read the Desktop guide - it will help to migrate to Ubuntu from windows.
Tell us which os is on which drive for a start!

---

### Post by atomic0x on 2007-04-02
It sounds like there might be a conflict with the drives.  If you haven't already done so I would recommend that you check the jumpers on the drive that you installed for Ubuntu to make sure that it is the only master or slave drive on the IDE cable.  If it is the only drive on the cable it should be master.

The error numbers you're getting from the grub documentation are:

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

This suggests to me that grub may be trying to mount your ntfs partition instead of your ext3 partition.

22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

Sounds like there was a partition available when grub was installed that is no longer available.  Likely because of a conflict.

Could you let us know what drives are attached to IDE0 and IDE1 on your mother board, and how they are jumpered (ie master/slave) as well as where the partitions are?

---

### Post by thenme on 2007-04-02
Currently I have two hard drives connected I can't tell you which is IDE0 or IDE1 In my bios it just names the device and they are identical drives.
The hard drive that has ubuntu loaded is partitioned three times like this

/dev/hdc1   *           1        9331    74951226   83  Linux
/dev/hdc2            9332        9729     3196935    5  Extended
/dev/hdc5            9332        9729     3196903+  82  Linux swap / Solaris

The other

/dev/hdd2   *           2        9729    78140160    5  Extended
/dev/hdd5               2        9729    78140128+  83  Linux

The drives are physically set to master / slave The master drive has ubuntu on it. Also when I installed ubuntu it was the only drive connected the the system

as you will no doubt see my master drive is named "hdc" this I find odd and the other drive is "hdd" again odd I thought that they should be "hda" and "hdb" and so on with the partitions having a number added at the end.

There are three other drives for the system but none of them are plugged in. Every time I plug one or any in the boot fails.
These drives are the drives that I have windows and all my files saved to
1st  SATA 250gib (Can be wiped out) I intended to use this drive as my primary Linux disc 
2nd SATA 500gib (can be formatted) I have moved everything off this drive.
3rd SATA 500gib (can't lose anything of this drive) Its full and ntfs formatted 

If it makes things easier for you guys I am willing to start over if its possible to get all these drives up and running the way I'd like with out losing whats on the 3rd SATA

again thanks

---

### Post by thenme on 2007-04-02
OK I changed the set to include all the drives. 
I went in to my bios and set the master IDE hard drive to boot 1st
I was able to boot right up with out a problem. 

My sudo fdisk -l shows the following

Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       28864   231850048+   7  HPFS/NTFS
/dev/sdc2           28865       29126     2104511+  83  Linux
/dev/sdc3           29127       30401    10241437+  82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9331    74951226   83  Linux
/dev/hdc2            9332        9729     3196935    5  Extended
/dev/hdc5            9332        9729     3196903+  82  Linux swap / Solaris

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd2   *           2        9729    78140160    5  Extended
/dev/hdd5               2        9729    78140128+  83  Linux


Any help on where to go from here.

I would like to use the sdc drive for my ubuntu install and all the rest for storage.
I need to be able to read/write to sda and sdb before I can change there format, the rest of the drives can be reformatted as needed. 
I wonder if you can tell me how to format a drive in ubuntu?

---

### Post by thenme on 2007-04-03
Update: 
To fix my problem I ultimately reinstalled ubuntu with all the drives plugged in. 
Istalled ntfs-3g and mounted all the drives. 
Then I used gparted to reformat the drives to ext3

For anyone that may be using Acronis OS selector in your windows intall and are trying to do a similer windows free install of ubuntu make sure you uninstall Acronis from windows first or you will have a corrupt MBR and be locked out of your system. I was not able to fix this and had to install ubuntu on a different drive. A reformat of the drive dose not clean the drive to boot up with just the GRUB.

---

