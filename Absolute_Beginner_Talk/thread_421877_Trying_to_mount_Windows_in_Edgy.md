---
title: "Trying to mount Windows in Edgy"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by dryder on 2007-04-24
Hi
Edgy.

Having been following the instructions at [http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)
to the point where I have installed ntfs-3g but not been game enough to update fuse, I am 'ready' to mount my windows partition. I have backed up /etc/fstab.

May I ask for help though in deciphering the instructions:
> If you want to mount /dev/hda1 is your windows partition you need to enter the following line in /etc/fstab file:

/dev/ /media/ ntfs-3g defaults,locale=en_US.utf8 0 0

You need to replace your partition and mount point with your details
Example

/dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

save and exit the file

For my Windows disk (Ubuntu is on /dev/hdb1), fdisk-l gives me:
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825       14593    86501992+   6  FAT16.

Sorry, but I can't seem to work out what > /dev/ /media/ ntfs-3g defaults,locale=en_US.utf8 0 0 and > /dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
should be with my table above.

Also, hda2 is unused and I want to use it in Ubuntu. Is there something I should do to permit this? Does hdA have to be before hdB in fstab? Can anybody enlighten me please?

Many thanks,
David

---

### Post by Happy_Man on 2007-04-24
Ok, put this in /etc/fstab:

> /dev/hda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0 

And get rid of the line: 

> /dev/hda1 * 1 3824 30716248+ 7 HPFS/NTFS

---

### Post by dryder on 2007-04-24
Thanks for replying Happy_Man,

As hda (ide1 master) was unplugged when I installed Ubuntu onto hdb, I don't have the entry > /dev/hda1 * 1 3824 30716248+ 7 HPFS/NTFS. to get rid of (I assume that's the reason the entry isn't there).

So do I just add > /dev/hda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0 before the entry:
# /dev/hdb1
UUID=a77cd4f7-f374-4724-95b6-226216ddf90c /               ext3    defaults,errors=remount-ro 0       1

This is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a77cd4f7-f374-4724-95b6-226216ddf90c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=da00e25d-8a86-4a84-84d9-97c33bb122a8 /data           ext3    defaults        0       2
# /dev/hdb2
UUID=ed97c2dd-00b4-49ff-bfc6-7206ea8c1692 /home           ext3    defaults        0       2
# /dev/hdd1
UUID=FAE4F5C2E4F580E5 /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=0088-2406  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4808736B087356C2 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=A628877928874771 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=8880A12E80A12422 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=DC6CB2456CB219EA /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=ae8b33e7-1f85-463f-b387-5c3af3ba352b /store          ext3    defaults        0       2
# /dev/hdb5
UUID=de3e64b8-8c5f-4145-8cc2-92de9b096fc0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Sorry I don't yet fully understand 'under the hood' settings like these.

David

---

### Post by Happy_Man on 2007-04-24
Well, go ahead and try it. Even if it is wrong, it's not major, it won't crash your system. It just won't mount that drive, that's how you tell it is working or not. After you add it and save your /etc/fstab, log out and then log back in to see if it works.

---

### Post by dryder on 2007-04-24
Hi Happy_Man,

It worked (thanks very much) fr the Windows partition.

1. How do I make it read-only, please?
I tried /dev/hda1/... uid=1000 0 0 instead of ...US.utf8 0 0 but it is read/write.

2.
To mount the unused fat16 partition I tried:
/dev/hda3 /media/windows vfat iocharset=utf8,umask=000 0 0
to automatically mount on boot up but this does not mount it.

Your (all) help is greatly appreciated.

David

---

### Post by Happy_Man on 2007-04-24
Uh... the point of ntfs-3g is to make it read/write. If you just wanted read-only, you didn't have to do anything; that's the default. If you want to mount your other partition, put this into a terminal:

```
mount /dev/hda1 /media/FAT-partition
```

---

### Post by dryder on 2007-04-24
Hi,
> 
Uh... the point of ntfs-3g is to make it read/write. Then I misunderstood it, for which I apologise. My problem was that nothing from that drive mounted - presumably **_only_** because it wasn't in fstab then.

Their documentation says:
> If you want to mount as read only you need to enter the following line in /etc/fstabfile
/dev/hda3 /media/windows ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0 which confused me (more).

My sincere apologies (are you able to point me to a manual on fstab - as this is not laziness but lack of finding info?)

So may I start again?
ide1 master (/dev/hda1 and /dev/hda2) was unplugged when Ubuntu was installed as I did not want the mbr interfered with - it is the setup I want until I can say goodbye to MS.

I want to auto-mount read-only /dev/hda1.
I want to auto mount (for Ubuntu's use) /dev/hda2.

You have just told me how to do the latter (mount /dev/hda1 /media/FAT-partition) so may I ask about the former (Windows) as read-only?

Presumably I can uninstall ntfs-3g if I don't want to write to the Windows partion?

I appreciate not only your help but your patience.

David

---

### Post by Happy_Man on 2007-04-24
Well, since you've gotten this far, why not just keep it as read/write? ntfs-3g certainly won't harm your system, and if you've got music or something on the Windows drive which you want to play in Ubuntu, some music players won't play them unless they have read/write access. And, could you post your backup /etc/fstab on here please? It's actually 10 PM here, and so I won't be back on until tomorrow. Just a heads-up.

---

### Post by dryder on 2007-04-24
Hi,

Many thanks - g'night. :-)

I didn't want any risk of corrupting Windows it is only the operating system partition. My programs and data etc. are on different partitions ond /dev/sd*x*.

Photoshop CS excepted ...

My backup file is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a77cd4f7-f374-4724-95b6-226216ddf90c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=da00e25d-8a86-4a84-84d9-97c33bb122a8 /data           ext3    defaults        0       2
# /dev/hdb2
UUID=ed97c2dd-00b4-49ff-bfc6-7206ea8c1692 /home           ext3    defaults        0       2
# /dev/hdd1
UUID=FAE4F5C2E4F580E5 /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=0088-2406  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4808736B087356C2 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=A628877928874771 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=8880A12E80A12422 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=DC6CB2456CB219EA /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=ae8b33e7-1f85-463f-b387-5c3af3ba352b /store          ext3    defaults        0       2
# /dev/hdb5
UUID=de3e64b8-8c5f-4145-8cc2-92de9b096fc0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

I would prefer /dev/hda2 to be useable from both Windows and Ubuntu if that is possible to make swapping files easy.

From down under - thanks.

David

---

### Post by Happy_Man on 2007-04-25
Then I would just keep it in read/write mode. It's easier, faster, the drivers are safe, and it saves us a bit more effort. :D

---

### Post by dryder on 2007-04-25
Hi (good evening?) Happy_Man,

Just woken up here ...

As you can see from my fstab file though, /dev/hda1 (ntfs) and /dev/hda2 (fat16) are not mounted.

So what should I put into fstab to auto mount both hda1 and 2 partions, please?

Many thanks,
David

---

### Post by Happy_Man on 2007-04-25
> /dev/hda1 /media/partiton_1 ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0 

/dev/hda2 /media/partition_2 vfat defaults, utf8,uid=1000 0 0 

I hope...

---

### Post by dryder on 2007-04-25
Hi,

Unfortunately they don't work ...

David

---

