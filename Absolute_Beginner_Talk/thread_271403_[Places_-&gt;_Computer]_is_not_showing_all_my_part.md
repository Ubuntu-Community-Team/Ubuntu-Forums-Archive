---
title: "[Places -&gt; Computer] is not showing all my partitions, can't proceed mounting NTFS..."
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Duccio on 2006-10-04
Hi all.

I am, at the moment, following the instructions at [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) in order to read files from my NTFS partitions. Here follows the output of *sudo fdisk -l*:

[I]Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2664    21398548+   7  HPFS/NTFS
/dev/sda2   *        2665        8776    49094640   83  Linux
/dev/sda3            8777        9039     2112547+   5  Extended
/dev/sda5            8777        9039     2112516   82  Linux swap / Solaris

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       10199    81923436    7  HPFS/NTFS
/dev/hdd2           10200       19457    74364885    f  W95 Ext'd (LBA)
/dev/hdd5           10200       19457    74364853+   7  HPFS/NTFS[/I]

As you see, I have two HDs, and the partitions I'd like to mount are */dev/hdd1* and */dev/hdd5*. None of them contain Windows, which is in the SATA HD. The very strange thing is that I'm **sure** I've seen those partitions from the File Browser window under *Computer*, than I booted Windows back and turned to ubuntu again in order to try mounting those partitions, but they were gone! I tried editing */etc/pmount.allow* anyway, but had no success. */etc/pmount.allow* looks like this now:

[I]# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
/dev/hdd1
/dev/hdd5[/I]

Here's a screenshot of how my *Computer* looks :-(

[[IMG]http://img501.imageshack.us/img501/7169/screenshotwu9.th.png[/IMG]](http://img501.imageshack.us/my.php?image=screenshotwu9.png)

I hope I gave enough information so you guys can help me solve this, it's probably something stupid/obvious because I'm using Linux since a couple of hours.

---

### Post by PPAAUULL on 2006-10-04
Have you or have you not mounted the windows partition?

---

### Post by Kateikyoushi on 2006-10-04
Please give me the output of this command:

```
cat /etc/fstab
```

---

### Post by Duccio on 2006-10-04
Here you are:```
cat /etc/fstab
``` returns:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

**PPAAUULL**: If I understood correctly what *to mount* means, I didn't mount and I don't want to mount */dev/sda1*, on which Windows lies.

---

### Post by PPAAUULL on 2006-10-04
You want files off of it right?

---

### Post by Kateikyoushi on 2006-10-04
You have to edit your fstab.
First backup.

```
sudo cp /etc/fstab /etc/fstab.bck
```

Create the mount folder

```
sudo mkdir /media/[NAME]
```

Replace name with whatever you describes well the partition, and repeat it one more time for the second one.

Then edit fstab.

```
gksudo gedit /etc/fstab
```

Add these lines

```
/dev/hdd1    /media/[NAME1] ntfs  nls=utf8,umask=0222 0    0
/dev/hdd5    /media/[NAME2] ntfs  nls=utf8,umask=0222 0    0

```

Then save it.

After a reboot it should work but you can type this instead.

```
sudo mount -a
sudo /etc/init.d/dbus-1 restart
```

---

### Post by Duccio on 2006-10-04
It works 50%: both partitions appear with their labels under *Computer*, but I could only mount hdd1 (which now appears on my desktop too): if I try to double-click the other one, the following message appears:

**Unable to mount selected volume.**
mount: only root can mount /dev/hdd5 on /media/partition2

The icon is also slightly different: hdd1 has the same icon as *Filesystem* while hdd5 has the same icon as the 20GB partition on my SATA, the one I don't want to mount, which now appears there too (not a problem at all: I'm just giving this information in case it's useful)

---

### Post by Duccio on 2006-10-09
(up)

---

### Post by anaconda on 2006-10-09
What happens if you try (in terminal):
sudo mount -t auto /dev/hdd5 /media/partition2

(assuming you already created the folder /media/partition2)

Oh. And this has nothing to do with your problem, BUT usually fixed disks are mounted to somewhere else than to /media.. eg. /mnt.. and only removable drives are mounted to /media, and therefor are visible on the desktop.. but do as you like.

---

### Post by Duccio on 2006-10-09
D'oh! It was my fault: there was a typo, I created /media/partition5 instead of /media/partition2, probably a typo using the numeric pad, editing /etc/fstab with right folder names just fixed everything. Thank you all for your help and time, and sorry for this error, I just thought some strange esoteric problems were occurring and didn't check the obvious things first.

---

