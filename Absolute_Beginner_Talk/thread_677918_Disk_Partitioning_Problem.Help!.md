---
title: "Disk Partitioning Problem.Help!"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by lemonicetea on 2008-01-25
Hi,,I met a problem about partitioning..
I have two hard drives installed on my PC,say driver A and B. My A driver is has four partitions with Windwos XP installed and Dish B has three partitions..say B1, B2 and B3. I install my Ubuntu 7.10 on B1. B2 is a NTSF partition and B3 is a FAT32 partition which is supposed exchange files between windows and Ubuntu. But recently I resize the B3 partition in WindowsXP. Unfortunately when I go back to Ubuntu i found the pre-mounted driver is gone...When I check the disk, it says 19GB.But actually It should only has 5.5G according to WindowsXP. Could anyone help? Thanks a lot....

---

### Post by taurus on 2008-01-25
While in Ubuntu, open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by lemonicetea on 2008-01-25
fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x697f9040

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2981    22531131   83  Linux
/dev/sda2            2981       15506    94687110    f  W95 Ext'd (LBA)
/dev/sda5            2982        3185     1542208+  82  Linux swap / Solaris
/dev/sda6            3186       14711    87136528+   7  HPFS/NTFS
/dev/sda7           14712       15505     6002608+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6773    51203848+   7  HPFS/NTFS
/dev/sdb2            6774       20055   100411920    f  W95 Ext'd (LBA)
/dev/sdb3           20056       20673     4672080   12  Compaq diagnostics
/dev/sdb5            6774       12191    40960048+   7  HPFS/NTFS
/dev/sdb6           12192       17338    38911288+   7  HPFS/NTFS
/dev/sdb7           17339       20055    20540488+   7  HPFS/NTFS

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=fad30bf0-4508-4241-8eef-57520bf7252d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=208009478009253E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=A4C0-E1D9  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=2E14CE0F14CDDA4B /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=0E4495EA4495D535 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=D090F40E90F3F8B4 /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=01C83C231130EC80 /media/sdb6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=20DF-5576  /media/sdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=d274243a-1845-4ea5-b2ec-dcd5e002fcdc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              22G  6.5G   14G  32% /
varrun               1014M   92K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  120K 1013M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1              49G   30G   19G  62% /media/sda1
/dev/sdb3             4.5G  3.9G  625M  87% /media/sda3
/dev/sdb5              40G   23G   17G  59% /media/sda5
/dev/sdb6              38G   34G  3.8G  90% /media/sda6
/dev/sdb7              20G   13G  6.8G  66% /media/sda7
/dev/sda6              84G   25G   59G  30% /media/sdb6

How can I mount it again? and set auto-mount at startup

---

### Post by thelatinist on 2008-01-25
I'm not sure I understand.  The situation you described in your first post doesn't relate to the situation on your drives at all.  /dev/sdb3 is not FAT32; the only vfat partition you have is /dev/sda7.  Could you tell us exactly which partition it is you're having trouble with?

Also?  /dev/sdb7 is a FAT32 partition, but it's being mounted as NTFS in fstab.

---

### Post by louieb on 2008-01-25
Did you say you resized the missing partition?
It could be that the UUID of that partition changed.
To check run the 
```
blkid
```command and compare the output with the UUID in /etc/fstab. 

If different replace the  UUID in /etc/fstab with the one from the **blkid** output.

---

### Post by lemonicetea on 2008-01-26
Sorry..It is sda7..

---

### Post by thelatinist on 2008-01-26
> **lemonicetea said:**
> Sorry..It is sda7..Okay, then, it's easy enough to fix.  The problem is that the partition is FAT32, but it's being mounted as NTFS.  Easy enough to fix. Backup fstab and open it for editing using the following commands:```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```Edit the line that currently reads:

```
UUID=D090F40E90F3F8B4 /media/sda7 ntfs defaults,umask=007,gid=46 0 1
```to read:```
/dev/sda7 /media/sda7 vfat user,utf8,fmask=0111,dmask=0000 0 0
```
That should be all you need!

**For future reference:** in general, this is how you mount a partition using fstab:

1) Use the following command to create a mount point for this drive (change *mountpoint* to a name that is not already in use and will be easy to recognize and remember):

```
sudo mkdir /media/*mountpoint*
```

2) Use the following command to back a back up of your fstab file in case something goes wrong:

```
sudo cp /etc/fstab /etc/fstab.bak
```

3) Use the following command to open fstab for editing:

```
sudo gedit /etc/fstab
```

Add one of the following line (depending on filesystem type) to your fstab to cause it to automatically mount (replace *sda#* with the name of the device you wish to mount and *mountpoint* with the mountpoint you created in step 1):

**For ext3:**
```

/dev/*sda#* /media/*mountpoint* ext3 defaults,errors=remount-ro 0 1
```

**For NTFS:**
```
/dev/*sda#* /media/*mountpoint* ntfs-3g defaults,nls=utf8,umask222 0 0
```

**For Fat32 or Fat16:**
```
/dev/*sda#* /media/*mountpoint* vfat user,utf8,fmask=0111,dmask=0000 0 0
```

**For reiserfs:**
```
/dev/*sda#* /media/*mountpoint* reiserfs nodev,nosuid 0 0
```

---

