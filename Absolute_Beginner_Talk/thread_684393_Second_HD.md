---
title: "Second HD"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Niloc on 2008-02-01
I have a 130 gig drive on my Gutsy AMD 64 system and I want to add another HD with Windows XP so I can dual boot.
I have tried modifing Grub but I simply cannot get the second drive to work.
My fstab says 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=12e6f068-45de-4f30-b082-dcb2fe52425a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=78c74295-d0e5-41ea-9a17-b35dbdba5f1b /home           ext3    defaults        0       2
# /dev/sda3
UUID=9ca6e8dc-7faf-46e1-a7e2-321e0f6a6592 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0

I have inserted the following into menu.lst

title         Windows XP
root          (hd1,0)
makeactive
chainloader   +1



What am I missing, when I try to boot the Windows system I get a single line of garbage and then the usual Windows 'DISK BOOT FAILURE etc' message.

Can anyone help?

---

### Post by wieman01 on 2008-02-01
Before we make any changes, a number of things... Please boot Ubuntu, plug in the device and run:
> sudo fdisk -l
What file format is the external drive? NTFS or FAT32?

How do you connect the new HD, via USB?

Please answer all these questions before we go ahead, so that we don't make things worse. Also make a safety copy of 'fstab':
> sudo cp /etc/fstab /etc/fstab_backup

---

### Post by Niloc on 2008-02-01
OK, I have done all that. 
sudo fDisk -i gave me 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   b  W95 FAT32
/dev/sda2            1217        9726    68356575    b  W95 FAT32
/dev/sda3            9727       10212     3903795   82  Linux swap / Solaris
/dev/sda4           10213       16291    48829567+   5  Extended
/dev/sda5           10213       11428     9767488+  83  Linux
/dev/sda6           11429       16291    39062016   83  Linux
colin@Desktop:~$

---

### Post by Rocket2DMn on 2008-02-01
That drive has NTFS on it, so the fstab entry should be
```
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
```

---

### Post by Niloc on 2008-02-01
OK, I have changed fstab accordingly.
I just realised I did not answer your question, the new drive is connected normally as am extra drive, ie it is installed the same as the Linus drive.

Do I need to reboot yet?

---

### Post by Rocket2DMn on 2008-02-01
No reboot is needed unless you're trying to get into windows.  You can mount the drive like so (first making sure its unmounted, which it should be)
```
sudo umount /media/hda1
sudo mount -a
```
I'm going to bed, so I'll check up on you in the morning.  Good luck!

---

### Post by Niloc on 2008-02-01
I re-booted just to see what happened and I got 
mount: unknown filesystem type 'ntfs-3g'

So I suspect there is a typo there somewhere.

I hope you had an excellent night's sleep, you are 12 hours behind I think, we are 7 hours in front of GMT....

I appreciate your efforts....

Colin

---

### Post by hyper_ch on 2008-02-01
try this in grub:

```

title Windows XP
root (hd0,0)
makeactive
chainloader +1

```

---

### Post by jan quark on 2008-02-01
try to download the needed software via the terminal

type this
```

sudo apt-get install ntfs-3g ntfsprogs
```

---

### Post by Niloc on 2008-02-01
No, it is not root (hd0,0), the first paramter is the Drive, starting at 0 and the second is the partition so it is root (hd1,0).

I installed the software so mount -l is quite happy now. But the second drive still will not boot!!

Close, but not quite there yet....

---

### Post by hyper_ch on 2008-02-01
you have two harddisks in it. One is a SATA drive (sda) and the other one is an IDE one (hda). Depending on how you setup his bios either one could be first. Without doubt Windows is installed on the first partition (hda1) so it's definitively (x,0).

And as (1,0) didn't work it seems likely that it should be (0,0)

---

### Post by Niloc on 2008-02-01
I started off with only Linux on the computer. I has never had any Windows on it.
I am trying to add a second drive which has Windows XP installed (by the local guru), the Linux has always been (0,0) so the new drive should be (1,0) should it not?

---

### Post by Niloc on 2008-02-01
To summarise my system and problem...

Computer A, new Desktop
Computer B, Wife's computer, only for games and karaoke...


Drive #1, the 360 gig Linux Gutsy in computer A
Drive #2 the one in computer B, windows XP which works OK
Drive #3 my new 80 gig drive the local guru put XP on last week

#1 boots perfectly on A
#2 will not boot on computer A but it is happy on computer B, #3 will not boot on either A or B

I want computer A with dual boot from #1 (Linux) and #3 (XP)

Computer B will stay with #2

I can see Drive #3 on the desktop, all the Windows files are there, it shows 72 gig of free space and seems OK. The only problem is how do I get to boot from it??

---

### Post by froy02 on 2008-02-02
Your bios setting have to be the 80 gb drive as the first boot hard drive. Then install grub in the MBR of that drive.  Here's a thread that will tell you how to install grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Niloc on 2008-02-02
I went to the post and followed the instructions exactly.Now all I get is 'Starting Up', I press enter and I get the Disk boot failure message', then I press Esc and I am back where I started... If I select Linux from the menu I get Error 22 :no such partition.
The only way I can get something is turn off, start again, reverse the hard drives so the SATA is first then it proceeds as before...

---

