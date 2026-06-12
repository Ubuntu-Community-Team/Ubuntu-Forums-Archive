---
title: "Mounting a second sata drive"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by madscot on 2007-04-02
Hi guys

I'm reasonably new to ubuntu and am very happy with it so far.

Heres my problem. I have installed a new sata drive in my system to increase my storage and have it split into 3 partitions 2 ntfs and 1 fat but am having trouble understanding how to edit my fstab config to do this.

Fdisk gives: 
```
Disk /dev/sda: 300.0 GB, 300089646592 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       36483   293041665    f  W95 Ext'd (LBA)
/dev/sda5               2       36483   293041633+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2      620181   312570720    f  W95 Ext'd (LBA)
/dev/sdb5               2      163039    82171120+   7  HPFS/NTFS
/dev/sdb6          163040      325579    81920128+   7  HPFS/NTFS
/dev/sdb7          325580      620181   148479376+   b  W95 FAT32

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         976     7839688+   7  HPFS/NTFS
/dev/hdc2             977        1106     1044225   82  Linux swap / Solaris
/dev/hdc3            1107        1275     1357492+   b  W95 FAT32
/dev/hdc4            1276       14593   106976835    f  W95 Ext'd (LBA)
/dev/hdc5            1276        4393    25045303+   7  HPFS/NTFS
/dev/hdc6            4394       13573    73738318+   7  HPFS/NTFS
/dev/hdc7           13574       14593     8193118+  83  Linux
```

And my fstab file looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc7
UUID=f5bfb652-1d76-489a-9bc6-41014bc53b5a /               reiserfs notail          0       1
# /dev/hdc1
UUID=E0A41E71A41E4A84 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc4
UUID=B22C-F7C9  /media/hdc4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=9A645CB3645C943B /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc6
UUID=CE2829FE2829E665 /media/hdc6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=EC84DA5684DA233E /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=9AECFF8DECFF61C5 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc3
UUID=78687771-2842-454d-ac5d-66af4869a81a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

I want to mount sdb5, sdb6 & sdb7 but am confused if the UUID part is important to mounting them or can i create the folders and add the appropriate lines to fstab?

Regards

Ms

---

### Post by taurus on 2007-04-02
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these three lines to the end of it.

```

/dev/sdb5   /media/sdb5   ntfs    defaults,nls=utf8,umask=007,gid=46   0    1
/dev/sdb6   /media/sdb6   ntfs    defaults,nls=utf8,umask=007,gid=46   0    1
/dev/sdb7   /media/sdb7   vfat    defaults,utf8,umask=007,gid=46   0    1

```
Save it.  Then, create three new mount points and mount them.

```
sudo mkdir /media/sdb5 /media/sdb6 /media/sdb7
sudo mount -a
df -h
```

---

### Post by madscot on 2007-04-02
Great thank you very much, i was beginning to go mad as all my music was on sdb5, but now it has been restored

Thanks again

Ms

---

