---
title: "harddrive help"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by reddragons13 on 2007-03-29
i have two hard drives  a sata that has windows xp and an ide that has unbutu.
i would like to play the media on the sata in unbutu but i cant find the drive.could i please get some help? 



amd 64 x2 4800
2 nvidia 7900 gt's  (sli)
250 gig sata2
40 gig ide (for unbutu)
2 gig ram corsair xms
asus a8n32 sli deluxe
water cooling

---

### Post by bodhi.zazen on 2007-03-29
> **reddragons13 said:**
> i have two hard drives  a sata that has windows xp and an ide that has unbutu.
i would like to play the media on the sata in unbutu but i cant find the drive.could i please get some help? 



amd 64 x2 4800
2 nvidia 7900 gt's  (sli)
250 gig sata2
40 gig ide (for unbutu)
2 gig ram corsair xms
asus a8n32 sli deluxe
water cooling

Show us the output of the following two commands :

sudo fdisk -l
cat /etc/fstab

---

### Post by reddragons13 on 2007-03-29
terry@terry-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4665    37471581   83  Linux
/dev/hdc2            4666        4866     1614532+   5  Extended
/dev/hdc5            4666        4866     1614501   82  Linux swap / Solaris


terry@terry-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=100ccda0-22c0-4ad4-9ef4-8fea589d235d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=193aefe9-6d5b-4c24-875d-73e3b7834b26 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by bodhi.zazen on 2007-03-29
OK you can go the easy way or the hard way.

Easy way  = gui ...

ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Hard way = CLI (IMO CLI is easier)

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
```

To have the partition mounted at boot, read only, add this line to fstab :

> /dev/sda1  /media/windows  ntfs auto,users,gid=100,uid=1000 0 0

After adding this line to fstab you can mount with :

```
mount -a
```

or

```
mount /media/windows
```

It should auto mount at boot.

If you want read-write, follow the link I gave you above.

---

### Post by reddragons13 on 2007-03-31
i put in /dev/sda1 /media/windows ntfs auto,users,gid=100,uid=1000 into the terminal but it said that i dont have permission

---

### Post by bodhi.zazen on 2007-03-31
> **reddragons13 said:**
> i put in /dev/sda1 /media/windows ntfs auto,users,gid=100,uid=1000 into the terminal but it said that i dont have permission

In a terminal use this :

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
```

The line : /dev/sda1 /media/windows ntfs auto,users,gid=100,uid=1000 0 0

Belongs in fstab ```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add the line (at the bottom of the file is OK) :> /dev/sda1 /media/windows ntfs auto,users,gid=100,uid=1000 0 0

Now you can mount the partition with : 

```
mount /media/windows
```

Also the partition should mount at boot.

---

