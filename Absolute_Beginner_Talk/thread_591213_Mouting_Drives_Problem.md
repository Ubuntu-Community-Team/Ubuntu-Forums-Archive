---
title: "Mouting Drives Problem"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by AnyaWest on 2007-10-25
Hiya all, I have problems with two of my hard drives. I'm currently running off the live CD and I can't install Ubuntu because it says my C drive (the one I want to install Ubuntu on) can't be mounted, because "NTFS is marked in use" it says I should go into windows to remove it, but my windows is messed up (hence why I'm trying Ubuntu), I can't get inside windows. It also won't let me mount my back up drive (D drive) for the same reason, however, my media drive (S drive) mounts fine, I tried typing in a code that Ubuntu gave me after trying to mount, but it just said "only root can do that", someone told me to put 'sudo' in front of it, but now I see this:

[I]ubuntu@ubuntu:~$ sudo mount device -t ntfs-3g /dev/hdb1 /media/data -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .[/I]

Now, I am very much a Linux noob and I just didn't understand any of that. I just want to install Ubuntu, copy files off my C drive I forgot to back up onto either my D or S drive, wipe windows clean and start again with duel booting. But being unable to get into my C drive to copy and also install Ubuntu, I can't do anything at the moment.

I would love some help on this, thankyou for your time :)

---

### Post by snickers295 on 2007-10-25
Linux isn't very good at NTFS partitions for some reason.
try [this]("http://www.arsgeek.com/?p=585") and see if you can mount the NTFS partition from there.

---

### Post by AnyaWest on 2007-10-25
Okay, I've tried that link but mine came back as this:

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93fd93fd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6158fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00010133

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      484518   244197040+   7  HPFS/NTFS
[/I]

It looks nothing like it is meant to on that website:

[I]Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20480008+ 7 HPFS/NTFS
/dev/sda2 2550 7493 39707451+ f W95 Ext’d (LBA)
/dev/sda3 7494 9729 17960670 83 Linux
/dev/sda5 2550 7394 38911288+ b W95 FAT32
/dev/sda6 7395 7493 795186 82 Linux swap / Solaris[/I]

So, once again, I think I'm stuck

---

### Post by snickers295 on 2007-10-25
do you remember how much free space was one that drive?
if it had enough free space for you to install ubuntu on you might try [gparted]("http://gparted.sourceforge.net/livecd.php") LiveCD to partition some free space off of the ntfs partition on the drive.

---

### Post by AnyaWest on 2007-10-25
Okay, but how will that help? My S drive is mounted, but that's NTFS, and my D drive can't be mounted but it won't be partitioned. I'm sorry for the maybe stupid question, but my head is hurting trying from to understand all this.

I also have a partitioning/booting program already installed on my PC that loads before windows, so I thought I could use that for partitioning and my duel booting.

---

### Post by snickers295 on 2007-10-25
> **AnyaWest said:**
> Okay, but how will that help? My S drive is mounted, but that's NTFS, and my D drive can't be mounted but it won't be partitioned. I'm sorry for the maybe stupid question, but my head is hurting trying from to understand all this.

I also have a partitioning/booting program already installed on my PC that loads before windows, so I thought I could use that for partitioning and my duel booting.
there is no stupid questions around here (accept for mine :lolflag:)
did the windows system have bad history of viruses?
how long ago did you do a defrag before it messed up?
linux can't edit ntfs partitions unless there clean.

---

### Post by AnyaWest on 2007-10-25
Haha, thanks :)

Well, my PC has never had viruses, but a long history of random problems, all sorts of bugs and errors on both the C and D drives (never the S drive). I cannot remember my last defrag, but it was a long time ago :|

So, there is no way of recovering my data from the C and D drives? If so, then the whole point of my back up D drive was an utter waste of time... agh, this is just so hard to get my head around everything, plus I may have lost all my data.

---

### Post by snickers295 on 2007-10-25
you would probably have to buy some $$$$ tool to get the data back.
don't worry, Linux may seem hard but its just like riding a bike (without wheels and with a CPU... bad example) but to make it seem easy, look back to the DOS days.

---

