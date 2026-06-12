---
title: "hd problam after instul 7.04"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by liopard on 2007-12-06
i tryed to instull the 7.04 vision aftrer it did not manag to fully instul it salf i tryed to start my computer and fund out 2 of my 4 hard disk i can go in to the ubuntu instad if using the 15 g + a 2 5 g porttions i maid for it wrote it salf on the athers and naw i cant opan or see whats insid all my work and things r on one of this disks how do i gat in to tham so i can ristor the data on tham:confused::(:confused::(:confused::(

---

### Post by Partyboi2 on 2007-12-07
Pardon?
I am having problems understanding all your short hand, can you please explain alittle better what the problem is you are having?

---

### Post by liopard on 2007-12-07
after instuling ubuntu 7.04 i cant see any thing in  two of my hard disk's it looks like ubuntu wrote over my master boot racord instad of instaling whar i prepard a plase for it . i think what i need to do is fing a way to re-write the boot racord agen some haw or find a way to see whats in tham using dos or some thing so i retrive the data . sorry abut the way i write but im dixlactic . sorry for the inconvinyans reeding this . hope u can halp

---

### Post by Partyboi2 on 2007-12-08
So are you saying that when you boot up your system, You do not have the option to select your other operating system at boot and that you need to fix the mbr?

---

### Post by liopard on 2007-12-08
yes it sims the ubuntu insald it salf one the baster boot racord of me windows and my data hard disks .infact right naw i have now computer any more bicos i dont want to format the hard disks bicos i need the data thats on it :(

---

### Post by Partyboi2 on 2007-12-08
this can help you setup grub so that you will have the option of choosing what operating system you want to boot into.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
By the way are you getting any error messages and if so what are they?

---

### Post by liopard on 2007-12-08
error lowding oporating sistam

---

### Post by Partyboi2 on 2007-12-08
Can you post the output of this from a terminal
```
fdisk -l
```

---

### Post by liopard on 2007-12-09
sorry iim sach a newbe im trying to do what u tald me to but un fotchunatly i do not now haw to opan a terminal or evan what is a terminal

---

### Post by overdrank on 2007-12-09
> **liopard said:**
> sorry iim sach a newbe im trying to do what u tald me to but un fotchunatly i do not now haw to opan a terminal or evan what is a terminal

The terminal is located under applications, accessories, terminal

---

### Post by liopard on 2007-12-09
I see the two hard disk one it sad it has 35.1~ the ather is 71.3~ both whare 80 gg disks probable not all is portiond right

ubuntu@ubuntu:~$ fdisk -1 
fdisk: invalid option -- 1 
 
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
ubuntu@ubuntu:~$ fdisk 
 
Usage: fdisk [-l] [-b SSZ] [-u] device 
E.g.: fdisk /dev/hda  (for the first IDE disk) 
  or: fdisk /dev/sdc  (for the third SCSI disk) 
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive) 
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by overdrank on 2007-12-09
That is a lower case L not a 1
```
fdisk -l
```

---

### Post by liopard on 2007-12-09
Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8ae434bf 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        9352    75119908+  83  Linux 
 
Disk /dev/sdc: 2048 MB, 2048901120 bytes 
64 heads, 63 sectors/track, 992 cylinders 
Units = cylinders of 4032 * 512 = 2064384 bytes 
Disk identifier: 0x35133513 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1         992     1999749+   6  FAT16

---

### Post by overdrank on 2007-12-09
> **liopard said:**
> Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8ae434bf 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        9352    75119908+  83  Linux 
 
Disk /dev/sdc: 2048 MB, 2048901120 bytes 
64 heads, 63 sectors/track, 992 cylinders 
Units = cylinders of 4032 * 512 = 2064384 bytes 
Disk identifier: 0x35133513 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1         992     1999749+   6  FAT16

Using that command in the terminal ```
sudo fdisk -l
``` should output something like this
example mine
 ```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3890    31246393+  83  Linux
/dev/sda2            3891       38889   281129467+   5  Extended
/dev/sda5            3891       16638   102398278+   b  W95 FAT32
/dev/sda6           16639       16893     2048256   82  Linux swap / Solaris

```

---

### Post by liopard on 2007-12-09
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 80.0 GB, 80032038912 bytes 
255 heads, 63 sectors/track, 9730 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x42044203 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         608     4883728+   5  Extended 
/dev/sda2             609        1824     9767520   83  Linux 
/dev/sda3            5100        9729    37190475    7  HPFS/NTFS 
/dev/sda4   *        1825        4958    25173855   83  Linux 
/dev/sda5               1         608     4883697   82  Linux swap / Solaris 
 
Partition table entries are not in disk order 
 
Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8ae434bf 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        9352    75119908+  83  Linux 
 
Disk /dev/sdc: 2048 MB, 2048901120 bytes 
64 heads, 63 sectors/track, 992 cylinders 
Units = cylinders of 4032 * 512 = 2064384 bytes 
Disk identifier: 0x35133513 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1         992     1999749+   6  FAT16

---

### Post by liopard on 2007-12-09
what dos all this say ? haw can i use it ?

---

### Post by liopard on 2007-12-10
still did not solve it i dint now what to do with the sudo fdisk -l info i m gating and haw to keep going with this data pleses halp have important data on it

---

### Post by overdrank on 2007-12-10
> **liopard said:**
> still did not solve it i dint now what to do with the sudo fdisk -l info i m gating and haw to keep going with this data pleses halp have important data on it

HI and I apologize I am having a hard time understanding what your issue is. I just jumped in to help with the command that was suggested. I believe you are having trouble mounting the additional drives on 7.04 Feisty. Maybe this link will help
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by liopard on 2007-12-10
wall not rilly or maiby yes i istuld the ubuntu and naw i cant go in to ether of my hard disks i need to some haw make me windows work and get in to me ather storag disk

---

### Post by liopard on 2007-12-10
if this is my - sudo fdisk -l - whare is my windows and haw can i get in to it and is thar a way to see whats in the scond disk

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80032038912 bytes 
255 heads, 63 sectors/track, 9730 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x42044203 

Device Boot Start End Blocks Id System 
/dev/sda1 1 608 4883728+ 5 Extended 
/dev/sda2 609 1824 9767520 83 Linux 
/dev/sda3 5100 9729 37190475 7 HPFS/NTFS 
/dev/sda4 * 1825 4958 25173855 83 Linux 
/dev/sda5 1 608 4883697 82 Linux swap / Solaris 

Partition table entries are not in disk order 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8ae434bf 

Device Boot Start End Blocks Id System 
/dev/sdb1 * 1 9352 75119908+ 83 Linux 

Disk /dev/sdc: 2048 MB, 2048901120 bytes 
64 heads, 63 sectors/track, 992 cylinders 
Units = cylinders of 4032 * 512 = 2064384 bytes 
Disk identifier: 0x35133513 

Device Boot Start End Blocks Id System 
/dev/sdc1 1 992 1999749+ 6 FAT16

---

### Post by Partyboi2 on 2007-12-10
just to let you know I am still learning about mounting, but this might atleast give you a start place.

To mount the Ntfs partition 
You will need to make a mount point:
```
sudo mkdir -p /media/ntfs
```then to mount it:
```
sudo  mount  -t ntfs -o nls=utf8,umask=0222 /dev/sda3 /media/ntfs
```to mount the 2nd disk Fat partition:
Make a mount point:
```
sudo mkdir -p /media/fat
```then to mount
```
sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sdc1 /media/fat
```to unmount ntfs
```
sudo umount /media/ntfs
```to unmount fat
```
sudo umount /media/fat
```To write to a ntfs partition you will need to install NTFS-config
```
sudo apt-get install ntfs-config
```See this for better understanding:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
I also suggest reading up on:
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
[http://www.arsgeek.com/?p=675](http://www.arsgeek.com/?p=675)
If all your data is ok, I suggest reintalling feisty but this time let it complete the install (atleast this is my understanding of what happened -refering to your first post)
Anyone else wanting to help feel free to jump in. Mounting is not my strong point :p

---

### Post by liopard on 2007-12-10
thanks i tryed it but im gating difrant things than writin in the artical here is what i got

ubuntu@ubuntu:~$ fdisk -l 
 
Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8ae434bf 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        9352    75119908+  83  Linux 
 
Disk /dev/sdc: 2048 MB, 2048901120 bytes 
64 heads, 63 sectors/track, 992 cylinders 
Units = cylinders of 4032 * 512 = 2064384 bytes 
Disk identifier: 0x35133513 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1         992     1999749+   6  FAT16 
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 80.0 GB, 80032038912 bytes 
255 heads, 63 sectors/track, 9730 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x42044203 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         608     4883728+   5  Extended 
/dev/sda2             609        1824     9767520   83  Linux 

 the problam is i do not now what to do with this info ... im sach a nuby its not funy but i need stap by stap halp if posabel

---

