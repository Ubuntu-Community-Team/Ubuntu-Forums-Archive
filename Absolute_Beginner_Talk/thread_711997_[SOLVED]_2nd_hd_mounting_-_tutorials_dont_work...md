---
title: "[SOLVED] 2nd hd mounting - tutorials dont work.."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by zetjee on 2008-03-01
Hi everybody,

I've installed 7.10 on a HD off 80 GB and I've got an empty disk of 20 GB which i want to use for my backup of the /home/user directory so the 8.04 release can have a clean install.

But somehow i cant mount the 20GB HD, not even after this: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Please help!

---

### Post by forestpixie on 2008-03-01
can you post 

sudo fdisk -l
cat /etc/fstab

---

### Post by zetjee on 2008-03-01
Gave me this: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=341beb7e-b41c-4495-b315-1b9823abfac4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b5e25588-b2ef-4864-b17d-7e3f4ceaa5df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Kan - niet openen (translated to english: can't open)

---

### Post by taurus on 2008-03-01
Can you post the output of the first command again?  Remember, it's a lower case letter L at the end, not number one.

```
sudo fdisk -l
```

---

### Post by zetjee on 2008-03-01
Schijf /dev/sda: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x2f492f48

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        9872    79296808+  83  Linux
/dev/sda2            9873        9964      738990    5  Uitgebreid
/dev/sda5            9873        9964      738958+  82  Linux wisselgeheugen

Schijf /dev/sdb: 20.0 GB, 20000000000 bytes
255 koppen, 63 sectoren/spoor, 2431 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xea1aa9c7

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1            2340        2431      738990    5  Uitgebreid
/dev/sdb5            2340        2431      738958+  82  Linux wisselgeheugen

---

### Post by MarkusIggy on 2008-03-01
I really need the answer for this, as I am also having this problem...
Anyone who knows?

---

### Post by taurus on 2008-03-01
> **zetjee said:**
> Schijf /dev/sda: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x2f492f48

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        9872    79296808+  83  Linux
/dev/sda2            9873        9964      738990    5  Uitgebreid
/dev/sda5            9873        9964      738958+  82  Linux wisselgeheugen

Schijf /dev/sdb: 20.0 GB, 20000000000 bytes
255 koppen, 63 sectoren/spoor, 2431 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xea1aa9c7

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1            2340        2431      738990    5  Uitgebreid
/dev/sdb5            2340        2431      738958+  82  Linux wisselgeheugen

Try 

```
sudo mkdir /media/sdb5
sudo mount -t ext3 /dev/sdb5 /media/sdb5
df -h
```

---

### Post by LuisGMarine on 2008-03-01
You might also have to give your users permission to write to that mount point.  Make sure the partition / hdd is not mounted and run

```
sudo chown -R <username>:<username> /media/sdb5
```

of  course substitute <username> with your actual user name.

---

### Post by zetjee on 2008-03-01
> **taurus said:**
> Try 

```
sudo mkdir /media/sdb5
sudo mount -t ext3 /dev/sdb5 /media/sdb5
df -h
```
Did this, and the dir /media/sdb5 was created. But when i typ df -h i get this: ```
Bestandssysteem            Grtte Gebr Besch Geb% Aangekoppeld op
/dev/sda1              75G  7,6G   64G  11% /
varrun                125M   84K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   68K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   91M  28% /lib/modules/2.6.22-14-generic/volatile

```
The mounting fails somehow. Even after chown it to my username i got the same result. 

An other solution?

---

### Post by taurus on 2008-03-01
Can you post the whole error message when you run this command?

```
sudo mount -t ext3 /dev/sdb5 /media/sdb5
```

---

### Post by zetjee on 2008-03-02
mount: apparaat /dev/sdb5 bestaat niet

translated: mount: device /dev/sdb5 doesnt exist

---

### Post by zetjee on 2008-03-02
I made a new partition on de hard drive and removed the old one. 

Next to that i typed ```
cd /dev
ls 
```
and saw a HD with the name: sdb1 tried to mount that. But didnt work either..

Please help.

---

### Post by zetjee on 2008-03-02
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Here was the anser. :) 

Thanks a lot everybody. :D

---

