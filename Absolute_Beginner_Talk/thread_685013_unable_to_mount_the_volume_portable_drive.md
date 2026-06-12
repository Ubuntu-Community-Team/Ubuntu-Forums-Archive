---
title: "unable to mount the volume portable drive"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by greendragonfire on 2008-02-01
I'm not entirely sure what happened...
I have a portable harddrive, which I use to store all of my pictures, music, and documents...
My brother took the harddrive over to his friends house to put his friends music on it, or something...  
I plugged it into the computer while it was on, but I don't think that that should have caused a problem.
My brother said he turned the computer off before he unplugged it.
But it is still showing up under Computer, so that means it wasn't unmounted before it was unplugged, right?
Anyway, I don't know how to forcibly unmount it, restarting the computer has no effect, and following the instructions under the Cannot Mount Volume popup has yielded no results, so help would be greatly appreciated.

Oh, and my computer is also refusing to recognize my mp3 player when I plug it in.

---

### Post by Rocket2DMn on 2008-02-01
Can you please post the output of
```
sudo fdisk -l
mount
```
that's a lowercase L on the first command.

---

### Post by greendragonfire on 2008-02-01
vanessa@vanessa-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b321b31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2405    19318131   83  Linux
/dev/sda2            2406        2498      747022+   5  Extended
/dev/sda5            2406        2498      746991   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9994b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 4975 MB, 4975370240 bytes
154 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 9548 * 512 = 4888576 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       81498      201053   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(81497, 41, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(201052, 16, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       17668      220436   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(17667, 80, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(220435, 70, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      195841      398609   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(195840, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(398608, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      302229      302235       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(302228, 132, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(302234, 103, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
vanessa@vanessa-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
vanessa@vanessa-desktop:~$

---

### Post by eapache on 2008-02-01
Assuming that the disk is /dev/sdc, it looks like it got corrupted. Try booting to windows and running a fix-disk on it.

---

### Post by greendragonfire on 2008-02-01
What about my mp3 player?

---

### Post by eapache on 2008-02-01
Was it plugged in when you ran those commands?

---

### Post by Rocket2DMn on 2008-02-01
It looks like sdc is the drive with problems.  I would suggest plugging it back into a windows computer and running a scandisk on it, then removing it safely.  Sounds like the partition table got messed up on the drive, and if it is formatted with NTFS, you should have windows try and fix it.
We could try to force an ntfs mount, but it doesn't even recognize that the drive is ntfs, so I don't want to do that yet.

---

### Post by greendragonfire on 2008-02-01
> **eapache said:**
> Was it plugged in when you ran those commands?

yeah, because I was checking to see if it still didn't work before asking about it.

---

### Post by eapache on 2008-02-01
How big is the external drive and the mp3 player?

---

### Post by greendragonfire on 2008-02-01
my external harddrive is 298 GB, and my mp3 player is 5 GB

---

### Post by greendragonfire on 2008-02-01
erm... this probably makes no difference, but the last time I hooked my mp3 player up to a computer was my friends mac.
For some reason, it was unable to mount it, so I unplugged it.

heh, maybe I should just quit bringing my hard drives over to other peoples houses.

---

### Post by eapache on 2008-02-01
Your hard drive is fine. Your MP3 player is messed up. To mount your hard drive```
cd /media
sudo mkdir External_Drive
sudo mount /dev/sdb1 /media/External_Drive
```The first line changes to the /media folder. The second creates the folder. The third mounts the disk inside the newly created folder. To unmount later```
sudo umount /dev/sdb1
```

---

### Post by greendragonfire on 2008-02-01
Thank you!

---

