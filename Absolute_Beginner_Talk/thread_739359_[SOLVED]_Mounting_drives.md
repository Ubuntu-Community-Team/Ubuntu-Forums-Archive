---
title: "[SOLVED] Mounting drives"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-03-29
I have my music and Vista partitioned on other parts of my hard drive, I was able to access  them just fine, I connected my ipod to transfer songs, during the transfer it had an error and froze my computer.  I held the power button until the computer shutdown, I rebooted the computer and now every time i try to access those drives it says "Cannot mount Volume".  How do I gain access to these drives again?

---

### Post by Joeb454 on 2008-03-29
You need to boot into Vista and then shut it down properly (i.e. by clicking shutdown ;))

ntfs-3g (the utility that allows you to read/write ntfs partitions) still has issues if the device wasn't shutdown cleanly :(

---

### Post by davec64 on 2008-03-29
Try:
```
sudo mount -a
```

You'll probably get an error. read the error message and it will suggest trying to force the mount. Copy the line of code it suggest to the prompt, then hit enter. Do this for each partition it failed to mount.

Hopefully now you should be able to access your windows partitions!

Generally this happens if Windows fails to shut down correctly or there was an error. If so Ubuntu won't mount the partitions. Hence having to force the mount. Next time you reboot they should have been mounted automatically as you've got pass the error!:)

---

### Post by sirisaac87 on 2008-03-29
I tried shutting down the computer, booting up in vista and then shutting down again and going back into ubuntu, but that didnt work.  I tried the command but nothing comes up when I type in that command.  Are there any other solutions to fix this problem?

---

### Post by Joeb454 on 2008-03-29
So after cleanly shutting down Vista, it still doesn't work? That's quite odd, it's usually something that's easily fixed

---

### Post by sirisaac87 on 2008-03-29
So is there any other way to fix this problem?

---

### Post by Joeb454 on 2008-03-29
There'll be a way, I'm looking for one now :) Passing the thread along to other members of the Beginners Team too :)

---

### Post by paultag on 2008-03-29
hey there sirisaac87.

Have you tried windows chkdsk? I don't know a lot about it. BUT you can try to run fsck ( linux ) on the part. I would assume that fsck would work with a Vista part, but I am not sure.

Give both a try,

Cheers,
Tag

---

### Post by Joeb454 on 2008-03-29
As an update to my previous post, my method if this happens is:

Boot Vista --> Login --> Shutdown.

My apologies :) I should've made that clearer

---

### Post by smurphy_it on 2008-03-29
You can try a "Force mount".  That will probably do the trick.

Here is an example I found, which should show you the syntax.  This is a USB external drive.

sudo mount -t ntfs-3g /dev/sdd1 /media/NTFS_USB

---

### Post by sirisaac87 on 2008-03-29
for some reason I cant get it to force mount, I am very new to Linux so it is probably something that I am doing...I think the drive im a trying to mount is sda2 but im not a 100%.  I am having a hard time with the commands to, when I put in sudo mount -t /dev/sda2 it just brings up alot of instructions but none of them seem to pertain to me. HELP!!

---

### Post by Joeb454 on 2008-03-29
Post the output of ```
sudo fdisk -l
``` That's a lower case L by the way :) And tell us the size of the drive you're trying to mount :)

---

### Post by sirisaac87 on 2008-03-29
This is everything that came up when I put in that command, the drive I am trying to mount is sda2.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d3c4d3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8056    64709788+   7  HPFS/NTFS
/dev/sda2           10546       14462    31463302+   7  HPFS/NTFS
/dev/sda3           14463       14593     1052226   d7  Unknown
/dev/sda4            8057       10545    19992892+   5  Extended
/dev/sda5   *        8057       10435    19109286   83  Linux
/dev/sda6           10436       10545      883543+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/dm-1: 66.2 GB, 66262823424 bytes
255 heads, 63 sectors/track, 8055 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 32.2 GB, 32218421760 bytes
255 heads, 63 sectors/track, 3917 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 1077 MB, 1077479424 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/dm-3p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/dm-3p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/dm-3p4          167628      167631       25817+  4c  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(336, 0, 17) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 89, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by sirisaac87 on 2008-03-29
mount: can't find dev/sda2 in /etc/fstab or /etc/mtab

-does this have anything to do with me not being able to mount this drive??

---

### Post by Joeb454 on 2008-03-29
I don't think you can mount to there, you can mount to /media though :)

---

### Post by sirisaac87 on 2008-03-29
how would I mount to media if the drive I am trying to mount is sda2.  Is there a specific command?

---

### Post by ajmorris on 2008-03-29
> **sirisaac87 said:**
> how would I mount to media if the drive I am trying to mount is sda2.  Is there a specific command?

you dont need mount -t

do the following:
```
1) sudo mkdir /mnt/sda2
2) sudo ntfs-3g /dev/sda2 /mnt/sda2
```

Note, the first command, you can make the directory what ever you want, sda2 is just an example (and you can do /media or /mnt it doesnt matter)

---

### Post by sirisaac87 on 2008-03-30
I tried both commands with mnt and media...neither worked..it says :

sirisaac@Bossman07:~$ sudo ntfs-3g /dev/sda2 /mnt/sda2
fuse: mount failed: Device or resource busy

or

sirisaac@Bossman07:~$ sudo ntfs-3g /dev/sda2 /media/sda2
fuse: mount failed: Device or resource busy

---

### Post by davec64 on 2008-03-30
Open fstab

```
sudo gedit /etc/fstab
```

Do you have an entry for dev/sda2 ?

It might be listed by UUID, if so use the following to list UUID's

```
 sudo vol_id -u device
```

If you haven't got an entry in Fstab for it you'll need to add it for the drive/partition to be auto-mounted at startup.

---

### Post by rkd on 2008-03-30
Do you have two threads running for the same problem? I don't know what the others think about that, but I think that's a bad idea. You should post a note in one of these threads asking people to stop using it and giving a link to the other thread.

---

