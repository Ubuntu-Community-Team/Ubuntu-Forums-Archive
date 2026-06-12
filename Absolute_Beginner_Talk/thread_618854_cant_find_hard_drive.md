---
title: "cant find hard drive"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by brash_vs on 2007-11-20
i installed studio and now i cant find my 2nd hard drive its a sata run off a controller card.  i was running ubuntu before and it put the partitions on the hard drive in the media folder. 

i know it knows its there because the device manager sees it and the partitions. is it somewhere else or do i need some drivers i forgot about to mount it.

if you need more info let me know what you need and i'll try to find it for you.

thanks

brash

---

### Post by taurus on 2007-11-20
Post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by brash_vs on 2007-11-20
what should that do. tried it and still cant find anything. can past print out if you want it.

---

### Post by taurus on 2007-11-20
Would be nice if you can post the outputs of those three commands.

---

### Post by brash_vs on 2007-11-20
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a117ad5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5338    42869744    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            5338       18086   102400000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           18086       30402    98927616    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa9eb4f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         353     2835441   82  Linux swap / Solaris
/dev/hda2             354        1933    12691350   83  Linux
/dev/hda3   *        1934        3513    12691350   83  Linux
/dev/hda4            3514        4870    10900102+  83  Linux
brash@brash:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b5dab429-90e9-471f-9c6d-bc04a3e7f8ba /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=3eaa05cd-bf39-4437-8e86-61d08a8ab979 /home           ext3    defaults        0       2
# /dev/hda3
UUID=554662ce-dfd5-4b64-b356-d0601bfa7b6c /linux2         ext3    defaults        0       2
# /dev/hda1
UUID=54b48f51-2b6f-4381-852a-6af7a0050764 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
brash@brash:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              12G  3.2G  8.2G  29% /
varrun                314M   76K  314M   1% /var/run
varlock               314M     0  314M   0% /var/lock
udev                  314M   96K  314M   1% /dev
devshm                314M     0  314M   0% /dev/shm
lrm                   314M   35M  279M  11% /lib/modules/2.6.22-14-rt/volatile
/dev/hda4              11G  169M  9.6G   2% /home
/dev/hda3              12G  159M   12G   2% /linux2


if i go into the start button ->system menu ->storage media    i can see them there but cant do anything with them is it because of the file format  and where are they in krusader.

when i try to mount them in storage media (konqueror) it says

hal-storage-fixed-mount-all-options refused uid 1000

---

### Post by taurus on 2007-11-20
I assume you want to mount /dev/sda1, /dev/sda2, & /dev/sda3.

Open a terminal and edit /etc/fstab

```
kdesu kwrite /etc/fstab
```
and add these lines to the end of it.

```
/dev/sda1   /media/sda1   ntfs-3g   defaults   0   0
/dev/sda2   /media/sda2   ntfs-3g   defaults   0   0
/dev/sda3   /media/sda3   ntfs-3g   defaults   0   0
```
Save it.  Now, install ntfs-3g driver, create those new mount points, and mount them.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1 /media/sda2 /media/sda3
sudo mount -a
df -h
```

---

### Post by brash_vs on 2007-11-20
where can i learn this linux.   any good books or mags i should get. glanced at the official ubuntu book. seemed a little begginer even for me but that was just a quick glance. would like to learn some terminal commands, compiling ect.. 

thanks

---

