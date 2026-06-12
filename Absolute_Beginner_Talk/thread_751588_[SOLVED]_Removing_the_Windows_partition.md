---
title: "[SOLVED] Removing the Windows partition"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by ethoxyethaan on 2008-04-10
Since ubuntu + crossover/wine does pretty much everything windows xp/vista can (and more) I have decided to get rid of the useless 30 GB of HD space.

now i know how to remove a partition and merge it with another one BUT, i know while deleting Linux from your system you first need to get rid of the grub loader or else your in trouble.

so my question is: if i just remove the Window partition using Gparted and merge my linux partition with it will there be any complications?

(windows partition is the first partition) 

thank you for your time and interests.

---

### Post by Oldsoldier2003 on 2008-04-10
> **ethoxyethaan said:**
> Since ubuntu + crossover/wine does pretty much everything windows xp/vista can (and more) I have decided to get rid of the useless 30 GB of HD space.

now i know how to remove a partition and merge it with another one BUT, i know while deleting Linux from your system you first need to get rid of the grub loader or else your in trouble.

so my question is: if i just remove the Window partition using Gparted and merge my linux partition with it will there be any complications?

(windows partition is the first partition) 

thank you for your time and interests.

should be no problems at all. If you do have a problem just fire up a 
[SuperGrub Live CD]("http://supergrub.forjamari.linex.org/")  and it will easily fix it.

---

### Post by ethoxyethaan on 2008-04-10
ok i removed it and rebooted.

my desktop took a long time to load for some reason.

now i notice the first partition is not mounted.

the mount point was /media/windows

how do i set a new mount point on my fresh formatted partition?

it says: "disk", on my desktop but there is no file in my /media (except the windows one)

---

### Post by Oldsoldier2003 on 2008-04-10
did you expand your partition or did you create a new one? If you created a new linux parttion you can edit your fstab to mount it. If your old windows partition is still in your fstab you should also remove it.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) is a good tutorial on fstab and if you need further help just holler, we're here to help

---

### Post by Rocket2DMn on 2008-04-10
You will need to edit your /etc/fstab file.  Please post the output of
```
sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk/by-uuid/
```
and we will help you set it up.  You probably have the original entry for windows there, but fiddling with the partition may have changed the necessary entry details.

---

### Post by ethoxyethaan on 2008-04-10
> **Oldsoldier2003 said:**
> did you expand your partition or did you create a new one? If you created a new linux parttion you can edit your fstab to mount it. If your old windows partition is still in your fstab you should also remove it.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) is a good tutorial on fstab and if you need further help just holler, we're here to help

i tried to expand it using Gparted, but because the second partition is being used for some rather important processes i cant dismount it. (so i cant expand it aswell)

```
nick@nick-laptop:~$ sudo fdisk -l

Schijf /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x00000080

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        3648    29302528+  83  Linux
/dev/sda2            3649        4864     9767520   83  Linux
/dev/sda3            4865        5168     2441880   82  Linux wisselgeheugen
/dev/sda4            5169        9729    36636232+  83  Linux
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=20654ec2-c7f2-4353-a53b-02143eb8e10a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=69f9a0b4-1e92-4da9-86f0-d2bbea5395ef /home           ext3    defaults        0       2
# /dev/sda1
UUID=AE947B97947B60AF /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=0a4ebd39-4085-4c93-a45d-1fbd60527046 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

```
totaal 0
lrwxrwxrwx 1 root root 10 2008-04-11 02:21 0a4ebd39-4085-4c93-a45d-1fbd60527046 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-04-11 02:21 20654ec2-c7f2-4353-a53b-02143eb8e10a -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-04-11 00:25 642d270f-8d3c-467e-863f-54370148a595 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-11 02:21 69f9a0b4-1e92-4da9-86f0-d2bbea5395ef -> ../../sda4
```

---

### Post by R6V2 on 2008-04-10
If your actually switching, I'd recommend just to format your computer, and reinstall Ubuntu with 100% of space, this may keep somethings like old windows stuff from coming back/ from being there.

*Note* You don't need any part of Windows on your system to Install Ubuntu.

If I would keep Ubuntu (I still have windows) Then that's what I'd do.

---

### Post by Oldsoldier2003 on 2008-04-10
> **ethoxyethaan said:**
> i tried to expand it using Gparted, but because the second partition is being used for some rather important processes i cant dismount it. (so i cant expand it aswell)

```
nick@nick-laptop:~$ sudo fdisk -l

Schijf /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x00000080

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        3648    29302528+  83  Linux
/dev/sda2            3649        4864     9767520   83  Linux
/dev/sda3            4865        5168     2441880   82  Linux wisselgeheugen
/dev/sda4            5169        9729    36636232+  83  Linux
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=20654ec2-c7f2-4353-a53b-02143eb8e10a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=69f9a0b4-1e92-4da9-86f0-d2bbea5395ef /home           ext3    defaults        0       2
# /dev/sda1
UUID=AE947B97947B60AF /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=0a4ebd39-4085-4c93-a45d-1fbd60527046 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

if you use the [GParted Live CD]("http://gparted-livecd.tuxfamily.org/")   you can expand it:
remove this line in order to remove the remnants of your ntfs partition then on boot it wont be looking for it.
```
# /dev/sda1
UUID=AE947B97947B60AF /media/windows  ntfs    defaults,umask=007,gid=46 0       1
```

---

### Post by ethoxyethaan on 2008-04-10
> **R6V2 said:**
> If your actually switching, I'd recommend just to format your computer, and reinstall Ubuntu with 100% of space, this may keep somethings like old windows stuff from coming back/ from being there.

*Note* You don't need any part of Windows on your system to Install Ubuntu.

If I would keep Ubuntu (I still have windows) Then that's what I'd do.

took me hours to configure everything correct, and im not a quitter :D.

Oldsoldier2003 i took a look at the guide and i will be rebooting to check if te partition mounts automatically now.

(only problem left is that /media/windows is still there (eventho i removed it)

EDIT: the partition is still not mounted automatically.

---

### Post by Oldsoldier2003 on 2008-04-10
> **ethoxyethaan said:**
> took me hours to configure everything correct, and im not a quitter :D.

Oldsoldier2003 i took a look at the guide and i will be rebooting to check if te partition mounts automatically now.

(only problem left is that /media/windows is still there (eventho i removed it)

to remove it just sudo rmdir /media/windows
Its just an empty mount point, it won't hurt anything to leave it, but cleaning it up will avoid confusion someday.

---

### Post by ethoxyethaan on 2008-04-10
> **Oldsoldier2003 said:**
> to remove it just sudo rm /media/windows
Its just an empty mount point, it won't hurt anything to leave it, but cleaning it up will avoid confusion someday.
nick@nick-laptop:~$ sudo rm /media/windows
rm: kan ‘/media/windows’ niet verwijderen: Is een map

translation: rm: can't remove '/media/windows' it is a file.

i will be back tomorrow to try out the live cd from gparted.

---

### Post by Oldsoldier2003 on 2008-04-10
> **ethoxyethaan said:**
> nick@nick-laptop:~$ sudo rm /media/windows
rm: kan ‘/media/windows’ niet verwijderen: Is een map

translation: rm: can't remove '/media/windows' it is a file.
sorry meant rmdir. but anyhow once your fstab is cleaned up you can remove it safely.

---

### Post by ethoxyethaan on 2008-04-10
> **Oldsoldier2003 said:**
> sorry meant rmdir. but anyhow once your fstab is cleaned up you can remove it safely.
that did the job, 

like i said ill be back tomorrow to test out the rest, 

if i cant get it to work myself ill bump this back up,

thanks for the help so far,
i hope some day ill be able to give help back at the community

---

### Post by Rocket2DMn on 2008-04-10
> **ethoxyethaan said:**
> i tried to expand it using Gparted, but because the second partition is being used for some rather important processes i cant dismount it. (so i cant expand it aswell)

```
nick@nick-laptop:~$ sudo fdisk -l

Schijf /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x00000080

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        3648    29302528+  83  Linux
/dev/sda2            3649        4864     9767520   83  Linux
/dev/sda3            4865        5168     2441880   82  Linux wisselgeheugen
/dev/sda4            5169        9729    36636232+  83  Linux
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=20654ec2-c7f2-4353-a53b-02143eb8e10a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=69f9a0b4-1e92-4da9-86f0-d2bbea5395ef /home           ext3    defaults        0       2
# /dev/sda1
UUID=AE947B97947B60AF /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=0a4ebd39-4085-4c93-a45d-1fbd60527046 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

```
totaal 0
lrwxrwxrwx 1 root root 10 2008-04-11 02:21 0a4ebd39-4085-4c93-a45d-1fbd60527046 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-04-11 02:21 20654ec2-c7f2-4353-a53b-02143eb8e10a -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-04-11 00:25 642d270f-8d3c-467e-863f-54370148a595 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-11 02:21 69f9a0b4-1e92-4da9-86f0-d2bbea5395ef -> ../../sda4
```

OK the UUID on your windows partition changed which could explain why it complains to you.  If you are going to grow your other partition to use up the empty windows partition, then just remove the entry from fstab by placing a # in front of the line, otherwise the UUID needs to be updated in fstab to match.  Posted below is the updated UUID, but I will comment the entry out by placing a # in front, under the assumption that you are going to grow your root partition to use that space
```
# /dev/sda1
#  UUID=642d270f-8d3c-467e-863f-54370148a595 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
```

You edit the file by running
```
gksudo gedit /etc/fstab
```

---

### Post by ethoxyethaan on 2008-04-10
the tread is solved. (my initial problem that is)

i did what soldier said and removed the 
```
# /dev/sda1
UUID=AE947B97947B60AF /media/windows  ntfs    defaults,umask=007,gid=46 0       1
```

then formatted the first partition to fat32 and ran the script that automatically mounts my partition (from the tutorial) 

thank you Rocket2DMn and soldier.

---

