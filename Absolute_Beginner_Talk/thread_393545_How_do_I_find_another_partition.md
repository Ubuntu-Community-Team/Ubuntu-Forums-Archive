---
title: "How do I find another partition?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Bungo Pony on 2007-03-25
Okay, so I used Gparted to create a couple more partitions on my other hard drive. Now how do I find it in the file browser? Do I have to configure it?

---

### Post by taurus on 2007-03-25
You need to mount them before you can access/use them.  Not sure what filesystem you formatted them so there are two guides, one for fat32/ntfs and the other for ext3.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Bungo Pony on 2007-03-25
I formatted them with ext3. They're sda3 and sda4 (yeah, I'm learning :) ):

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         892     7164958+  27  Unknown
/dev/sda2   *         893        3442    20482875    7  HPFS/NTFS
/dev/sda3            3443       16203   102502732+  83  Linux
/dev/sda4           16204       20023    30684150   83  Linux

Disk /dev/hdb: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         752     6040408+  83  Linux
/dev/hdb2             753         788      289170    5  Extended
/dev/hdb5             753         788      289138+  82  Linux swap / Solaris

---

### Post by taurus on 2007-03-25
In that case, open a terminal and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/sda3   /media/sda3   ext3   defaults   0   1
/dev/sda4   /media/sda4   ext3   defaults   0   1
```
Save the changes.  Then, create a two new mount points and mount them.

```
sudo /media/sda3 /media/sda4
sudo mount -a
df -h
```

---

### Post by Bungo Pony on 2007-03-25
Is this right? I don't think those two are supposed to be the same size.

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             5.7G  2.7G  2.8G  49% /
varrun                221M   84K  221M   1% /var/run
varlock               221M     0  221M   0% /var/lock
procbususb             10M  164K  9.9M   2% /proc/bus/usb
udev                   10M  164K  9.9M   2% /dev
devshm                221M     0  221M   0% /dev/shm
/dev/sda3              29G  173M   28G   1% /media
/dev/sda4              29G  173M   28G   1% /media


Also, quick question, how do you delete folders in terminal?

---

### Post by taurus on 2007-03-25
You suppose to mount **/dev/sda3** to **/media/sda3** and **/dev/sda4** to **/media/sda4** as I described above.

```
rmdir **directory**
-or-
sudo rmdir **directory**
```

---

### Post by Bungo Pony on 2007-03-25
looks like I got it, but how do I remove what I messed up?

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             5.7G  2.7G  2.8G  49% /
varrun                221M   84K  221M   1% /var/run
varlock               221M     0  221M   0% /var/lock
procbususb             10M  164K  9.9M   2% /proc/bus/usb
udev                   10M  164K  9.9M   2% /dev
devshm                221M     0  221M   0% /dev/shm
/dev/sda3              29G  173M   28G   1% /media
/dev/sda4              29G  173M   28G   1% /media
/dev/sda3              97G  367M   91G   1% /media/sda3
/dev/sda4              29G  173M   28G   1% /media/sda4

---

