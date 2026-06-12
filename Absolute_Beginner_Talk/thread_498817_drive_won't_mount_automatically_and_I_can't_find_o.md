---
title: "drive won't mount automatically and I can't find opera"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-07-11
K I got this new drive right? I just got it formatted and I put all my stuff on it etc and it's ready for use. Ubuntu detects it when I start up. I double click on it in Computer and it brings up a password. I put it in and done. I see everything and a icon is placed on the desktop. Hunky dory except I have to do this every single time I start ubuntu. Can I get this done easily like guially or does it require sudo mount/dksjf/dlkfj/sdkjf -a? I've had problems in the past with the latter. Why can't they make it easy like windows and put it in, and full accessibility. It makes everyone happy.

Also. I remember seeing Opera web browser in add/remove software. Now I look for it cuz I think I like it more than FF but it no there. I lookit up in SPM and it's no where to be found. Where'd it go? Did it get deleted from the repositories.........I don't know what repositories mean but something had to happen to it.

---

### Post by Inxsible on 2007-07-11
About the drive problem, if its an external drive you should use pmount to mount it.

pmount will mount it under /media and automatically mount it everytime you connect it. If you dont have pmount installed you can install it by
```
sudo aptitude install pmount
```

then use it by
```
sudo pmount /dev/Xd*? MOUNT_POINT
```where X = s or h
* = a,b,c....
? = 1,2,3...

Post back if you need more help.

if its an internal drive, you need to place an entry for it in the fstab.

Tell me which one it is..so i can post a solution for you depending on whether its an internal or external drive.

---

### Post by linuxwizard on 2007-07-11
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by Yellowbelly on 2007-07-11
internal.

thanks.

---

### Post by Inxsible on 2007-07-11
> **Yellowbelly said:**
> internal.

thanks.

ok post the output of the following command

```
sudo fdisk -l
```-l is lowercase L

also point out the drive that you want to mount and where do you want to mount it(if you have decided on a specific mount point)

Generally, internal drives are mounted under /mnt and external under /media. Thats how i like it, but there are of course no restrictions

---

### Post by Yellowbelly on 2007-07-11
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       15017   120624021    b  W95 FAT32

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       11869    95337711    b  W95 FAT32
/dev/hdd2           11870       18804    55705387+  83  Linux
/dev/hdd3           18805       19457     5245222+  82  Linux swap / Solaris





I'ts the 120gb hdb although it says 115 in Computer. huh

---

### Post by Inxsible on 2007-07-12
> **Yellowbelly said:**
> Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       15017   120624021    b  W95 FAT32

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       11869    95337711    b  W95 FAT32
/dev/hdd2           11870       18804    55705387+  83  Linux
/dev/hdd3           18805       19457     5245222+  82  Linux swap / Solaris

I'ts the 120gb hdb although it says 115 in Computer. huh
```
gksudo gedit /etc/fstab
``` Add the following line to your fstab
```
/dev/hdb1 /media/120GB vfat defaults,auto,users 0 0
```Save and close the file. You can choose any other name instead of 120GB. However, if you have spaces in the name you will have to enclose it within quotes. My advice : Choose a name without spaces. Then
```
sudo mkdir /media/120GB
```
```
sudo mount -a
```

That should do it !!

---

