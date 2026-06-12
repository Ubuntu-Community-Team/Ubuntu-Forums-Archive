---
title: "Cannot see all Hard Drives"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by spe05081 on 2008-01-01
Hi,
I cannot see all my hard drives in Gutsy Gibbon.  I have 3 physical hard drives:

1. 80GB: 
Parition 1 for WinXP (NTFS), 
Partition 2 for Ubuntu (ext3)
2. 250GB labelled DATA (SATA, NTFS)
3. 250GB labelled BACKUP (IDE, NTFS)

I can see 1 and 2 **but NOT 3**.  I would like to have all drives to be immediately available, any suggestions?

*************
thomasps@GAZELLE:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31653164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       30401   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31233122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6987    56123046    7  HPFS/NTFS
/dev/sdb2            6988        9609    21061215   83  Linux
/dev/sdb3            9610        9729      963900    5  Extended
/dev/sdb5            9610        9729      963868+  82  Linux swap / Solaris

Disk /dev/hdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1e579d7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           2       30515   245103705    f  W95 Ext'd (LBA)
/dev/hdc5               2       30515   245103673+   7  HPFS/NTFS
***********************

---

### Post by taurus on 2008-01-01
You mean you can't see this one.

```

Device Boot Start End Blocks Id System
/dev/hdc1 * 2 30515 245103705 f W95 Ext'd (LBA)
/dev/hdc5 2 30515 245103673+ 7 HPFS/NTFS

```
Have you tried to add an entry in /etc/fstab to mount /dev/hdc5 when you boot Ubuntu?

```
cat /etc/fstab
```

---

### Post by spe05081 on 2008-01-01
Bear with me I'm fairly new...
The problem is, having 2 250GB drives I don't know which is being recognized/mounted and which isn't.  It does mount one of them but I need both.
I haven't modified fstab

---

### Post by taurus on 2008-01-01
Can you post the outputs of these commands?

```
cat /etc/fstab
df -h
```

---

### Post by spe05081 on 2008-01-01
Here it is...
******************
thomasps@GAZELLE:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3fb91940-85a0-46c4-a37f-889f6246f051 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f7241458-abfb-47c8-8a9f-96ad3316d598 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


thomasps@GAZELLE:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              20G  2.9G   16G  15% /
varrun               1008M  216K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  108K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  971M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5             233G  172G   62G  74% /media/DATA
/dev/sdb1              54G   15G   40G  27% /media/disk
*****************

---

### Post by taurus on 2008-01-01
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdc5
sudo mount -t ntfs-3g /dev/hdc5 /media/hdc5
df -h
```

By the way, can you also post the output of this command since there is a little odd thing in your /etc/fstab, /dev/sda5 as swap but it should have been your ntfs partition.

```
free
```

---

### Post by spe05081 on 2008-01-01
Thanks for your help taurus.  While I try the codes u gave, here is the output from free

*****************
thomasps@GAZELLE:~$ free
             total       used       free     shared    buffers     cached
Mem:       2063616     994732    1068884          0      47968     472044
-/+ buffers/cache:     474720    1588896
Swap:       963860          0     963860
******************

---

### Post by taurus on 2008-01-01
I guess it's just a typo in /etc/fstab but I am sure the UUID for the swap partition is right or else the system will complain about it when it boots up.

---

### Post by spe05081 on 2008-01-01
Ok, something is not working.  After updating and installing ntfs-3g I get the following:

***********************
thomasps@GAZELLE:~$ sudo mkdir /media/hdc5
mkdir: cannot create directory `/media/hdc5': File exists
thomasps@GAZELLE:~$ sudo mount -t ntfs-3g /dev/hdc5 /media/hdc5
Failed to access '/dev/hdc5': No such file or directory
thomasps@GAZELLE:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              20G  2.9G   16G  15% /
varrun               1008M  220K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  108K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  971M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5             233G  172G   62G  74% /media/DATA
/dev/sdb1              54G   15G   40G  27% /media/disk
**********************

---

### Post by taurus on 2008-01-01
Do you still have windows on your machine (which partition does it on anyway, /dev/sdb1)?

Boot into windows and run a scandisk or defrag on /dev/hdc5 to see if there is anything wrong with that drive.

Do you have any important files on /dev/hdc5?

---

### Post by spe05081 on 2008-01-01
Yes I'm dual booting winXP and ubuntu.  Both work fine.  Will defrag+run scandisk and let u know.  Thanks.
IShould I start worrying?

---

### Post by spe05081 on 2008-01-01
I tried booting into the ubuntu live cd and used gparted to look at my drives.
The drive I want to be able to mount is hdc5.  Gparted indicates:

*************
ERROR(2): failed to check '/dev/hdc5' mount state: No such file or directory
[...]
Probably /etc/mtab is missing.  It's too risky to continue. [...]
Unable to read the content of this filesystem!
*************
So I booted into windows and scheduled a checkdisk on the drive (with bad sector recovery). When that was done (2 hrs later), I defragged the drive.  Finally booted again into Ubuntu (not the Live CD this time) and installed gparted. It indicates a similar error (unable to read the content of this file system).

I can try reformatting the hard drive if necessary.  I wonder if the fact that the drive is an IDE as opposed to all the other drives being SATA may have something to do with this.
Any suggestions?

---

### Post by lovecrime on 2008-04-12
I've the same problem 
I've a 250 HD and a 80 HD 
the 80 says in GParted :
unable to read the content of this filesystem
Because of this some operations may be unavailable.

and there is an error flag beside the partions in the 80 HD 

any help ??

---

