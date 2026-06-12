---
title: "Advice re Grub and Partition Numbers"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by menawollas on 2006-06-18
Hi, 

I have just been installing Ubuntu and Windows Vista Beta 2 on a PC with a main OS of Windows XP (for evaluation - and I have to say that Ubuntu knocks the Sh*t out of Vista for an out of the box install).

Anyway, I repartitioned my drive as follows

P1    NTFS   Primary    XP
P2    NTFS   Primary    Vista
P3    Extended
P4    FAT32  Logical     Data
P5    NTFS   Logical     Data
P6    NTFS   Logical     Data
P7    ext2    Logical     Ubuntu /
P8    swap   Logical

First I created P2, and installed Vista on it as the active partition - boots fine.
Then I made P1 active and booted XP - boots fine.

Then I installed Ubuntu. Grub installs, but just gives two OS Ubuntu on hd0,7 and XP on hd0,1.   Both boot fine.

From what I understand, partitions should start numering at 0, with the first logical one always being 4 - so I can see that Ubuntu should be hd0,7 as its the 4th Logical partition - but surely XP should have been hd0,0 ?

Now heres the tricky bit - when I edit the grub menu, and include a line to boot hd0,0 then this will boot vista! 

So evrything is fine, but my question is why does

hd0.0 boot physical partition 2 and
hd0,1 boot physical partition 1

when surely it should be the other way round :confused: 

Thanks

---

### Post by lepre on 2006-06-18
maybe the answer was said by you: "First I created P2"

sound stange too...hd0,0 must be the first partition for sure. so the only one i can see is that!

---

### Post by Rui Pais on 2006-06-18
lepre is right, 
partitions made by Windows tools tends to follow the order of creation, not the disk order.
You can check it anyway by doing

sudo fdisk /dev/hda
and then hoose option 'p'

---

### Post by menawollas on 2006-06-18
Well, the XP partition P1, was there already, and is definately the first on the disk according to Partition Magic ??

---

### Post by lepre on 2006-06-18
try to run the disks app in ubuntu
system->disks
chech in the Partitions tab your configuration and tell us if there is any news

---

### Post by menawollas on 2006-06-19
The fdisk results are ..

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            1287        2624    10747485    7  HPFS/NTFS
/dev/hda2   *           1        1286    10329763+   7  HPFS/NTFS
/dev/hda3            2625       14946    98976465    f  W95 Ext'd (LBA)
/dev/hda5            2625        5074    19679593+   b  W95 FAT32
/dev/hda6            5075        8276    25720033+   7  HPFS/NTFS
/dev/hda7            8277       12334    32595853+   7  HPFS/NTFS
/dev/hda8           12335       14815    19928601   83  Linux
/dev/hda9           14816       14946     1052226   82  Linux swap / Solaris

and according to system/disks/partitions then 

partition 1 is mounted on /media/hda1 and 
partition 2 on /media/hda2 

So I'm still confused as to why its /dev/hda2 at the start of the disk ?

---

### Post by lepre on 2006-06-19
[QUOTE=menawollas]The fdisk results are ..
```

   Device Boot      Start         End      Blocks       Id System
/dev/hda2   *           1        1286    10329763+   7  HPFS/NTFS

```

and according to system/disks/partitions then 

partition 1 is mounted on /media/hda1 and 
partition 2 on /media/hda2 

So I'm still confused as to why its /dev/hda2 at the start of the disk ?[/QUOTE]

now we know that your "p2" is infact p1 :D
how it happend i really don't know? which program you used to make the partitions?

---

### Post by menawollas on 2006-06-19
Partition Magic 8.

Prior to  starting, I had a small 'dummy' partition as the first on the drive, with XP as the second. 

I deleted the dummy, shoved XP to the start, shrunk a few logical partions and pushed  the Extended one back in order to create the space I used to create the vista partition. (all seperate events, rather than everything as a batch).

Looks like moving the XP partition kept it as P2 even though it now starts at the start of the disk.

---

### Post by Rui Pais on 2006-06-19
hi,
(repeating my self,) some tools on Windows and PartitionMagic don't reorder the numeration of partitions on  disk after create a new one. The one maked 1st will be the hda1 for fstab, no matter how many you put later before that, and so on... To that tools numeration will follow order of creation. 
parted/gparted/qparted don't do that (I think... i use cfdisk and mke2fs -j). 

If you want to reorder, open fdisk, enter 'x' for advanced options, then 'f' for fix partition order, then 'w' to write and exit. **Then you need to change /etc/fstab ang /boot/grub/menu.lst** to new names. 

And NOTE: Maybe your Windows will not like that change or even stop to boot (which is in fact a good thing ;)). 

Leave it that way if you can boot everything and want to stay that way. Thats not an error. It's only a caracteristic of your particular partition table.

---

### Post by menawollas on 2006-06-19
Thanks for the answer, it looks like its not dire, just an annoyance for those that like things tidy.

Think I'll leave it till I wipe the drive and start from scratch !

---

### Post by lepre on 2006-06-19
[QUOTE=menawollas]Thanks for the answer, it looks like its not dire, just an annoyance for those that like things tidy.

Think I'll leave it till I wipe the drive and start from scratch ![/QUOTE]

i would do that too 8-)

---

