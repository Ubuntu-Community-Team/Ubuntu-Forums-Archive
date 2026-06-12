---
title: "Gnome hangs"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by nlbs on 2007-10-18
I thought to install Debian (multi boot) and during Installation I replaced Ubuntu grub with debian's one every thing works fine. But To Install Debian I deleted 2 partition and make them 1 partition (EXT2) and then I installed on it. as debian's /ec/fstab is generated dynamically during installation it works fine. But Ubuntu's /etc/fstab goes wrong. this is the output of fdisk```
# fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3202    25720033+  83  Linux
/dev/sda2   *        3203        5130    15486660    c  W95 FAT32 (LBA)
/dev/sda3            5131        9729    36941467+   5  Extended
/dev/sda5            5131        5783     5245191    b  W95 FAT32
/dev/sda6            5784        7711    15486628+  83  Linux
/dev/sda7            9498        9729     1863508+  82  Linux swap / Solaris
/dev/sda8            7712        9497    14346013+  83  Linux

Partition table entries are not in disk order

``` and this is Ubuntu's /etc/fstab```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c21137a0-e058-4758-a465-d972fb88d75c /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=fae0a489-a8fc-4764-9e44-2a7cad0caaef /entertainment  ext2    defaults        0       2
# /dev/sda2
UUID=647C-E810  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=469F-AB39  /media/sda5     vfat    defaults,utf8,umask=000,gid=1000,uid=1000   0       1
# /dev/sda7
#UUID=469F-A6E7  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
#UUID=469F-A6E8  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=d3b88bdc-13bf-492f-b5c4-9f81c7af53ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```To be honest I've no idea what does all this **UUID **means I'll appreciate If some one tells me what does this mean. somebody plese help me out. from this situation.
NOTE : 
when I start ubuntu in CLI mode it starts (Probably without mounting all partitions) but when I enter in GUI mode e.g. start gdm I can login gnome -panel starts, desktop wallpapers loads and then while loading icons it just hangs. remember it shows the mounted partitions on desktop as an icon.

---

### Post by mikeyphi on 2007-10-18
UUID is just a 'new' identification system - don't worry about it - the 'old' names are above e.g. # /dev/sda1

try - open a terminal and enter 'update-grub'

From your printout it looks like your Ubuntu has bad info for sda7;sda8;sda9
If update-grub doesn't work - try to edit those entries to match the output of your fdisk printout

---

### Post by erginemr on 2007-10-18
I cannot comment on your main problem, but I can tell you some about UUID.



It is the new way of representing hard drives in Linux. So when you look at the following chunk of data:

# /dev/sda1

UUID=c21137a0-e058-4758-a465-d972fb88d75c / ext2 defaults,errors=remount-ro 0 1



you will see that the part /dev/sda1 has been commented out, and has been replaced by UUID=...

You may list the correct uuid's by issuing: the command "blkid" from the console. You may check and correct the UUID's of all devices. 

However, as mikeyphi has pointed out, UUID is not something essential for the health of the system. You may try removing them from your /etc/fstab file and uncomment the /dev/sdx lines as in the following:
/dev/sda1  /  ext2 defaults,errors=remount-ro 0 1

But take a backup of the original fstab file first with:
sudo cp /etc/fstab /etc/fstab.orig
in case something goes wrong.

Let's see if this little trick will bring Gnome back.

---

### Post by nlbs on 2007-10-20
I've made the solution. the problem was swap was getting mounted wrongly and sda6 and above were also wrong. now the problem is vol_id is returning all UUID except the swap partition. So I used traditional /dev/sdaX for the swap.
Now everything is perfect.
But Why vol_id was not showing the uuid of the swap partition ?
and why UUID is better than traditional /dev/sdaX ?

---

### Post by erginemr on 2007-10-23
I often make beckups and restores via archiving (tar.gz) by whole drive. And I always have UUID issues whenever I mess up my system and restore from a previous backup. Then goes the usual vol_id checks, correcting the UUID's of the mounted partitions, etc.

After several such issues, I have decided to toss away UUID's once and for all, and return to the classical /dev/sdx mounting system and have not had any more problems ever since. And I did not have any performance impact after switching to the old system.

---

### Post by nlbs on 2007-10-23
Aha! Today I learnt something new.
Go to /dev/disk/by-uuid
you will see all the UUID's there no need to vol_id.
Right click and choose Arrange by Modification Time.
all the UUID are arranged serially.

---

