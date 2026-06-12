---
title: "External Harddrive problem"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by boichukj on 2006-03-02
Hi
Im trying to get into my 2 external HDD partitions they are both NTFS and I keep getting a message saying that i dont have the permissions necessary to view the contents.

Can someone please help?

Thanks

---

### Post by TrendyDark on 2006-03-03
NTFS isn't supported well under Linux. You can [COLOR="Red"]_**ONLY**_[/COLOR] view files on a NTFS drive.

To view them, check out this guide: [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by boichukj on 2006-03-04
Thanks for the help but for some reson it will only load my windows ntfs partition off of hda1.  It still gives me an error when i try to mount my external harddisk.  
Any suggestions?

---

### Post by Mustard on 2006-03-04
What we really need to troubleshoot this problem is the output of this command..

```
sudo fdisk -l
#this will show all your partitions/drives and what file format they are in
```

and the contents of your /etc/fstab file

```
cat /etc/fstab
#displays the contents of /etc/fstab
```

Post the output of both these commands and enclose them in the forum codes like this..

[noparse]```
..your text in here...
```[/noparse].

---

### Post by boichukj on 2006-03-05
Ok here is the output from the fdisk -l
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14         270     2064352+  82  Linux swap / Solaris
/dev/hdb3             271       24792   196972965   83  Linux

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8107    65119446    7  HPFS/NTFS
/dev/sda2            8108       24321   130238955    7  HPFS/NTFS

```
and here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                <dump>  <pass>

#FIRST INTERNAL HADDISK (WINDOWS PARTITION)
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0

#SECOND INTERNAL HARDDISK
/dev/hdb1       /boot           ext2    defaults                   0       2
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb2       none            swap    sw                         0       0

#EXTERNAL FIREWIRE DRIVE
/dev/sda1       /media/sda1     ntfs    nls=utf8,umask=0222        0       0
/dev/sda2       /media/sda2     ntfs    nls=utf8,umask=0222        0       0

#CDROM DRIVES
/dev/hdd        /media/cdrom0   auto user,noauto                   0       0
/dev/hdc        /media/cdrom1   auto user,noauto                   0       0

#FLOPPY DRIVE
#/dev/fd0        /media/floppy0  auto    rw,user,noauto            0       0

proc            /proc           proc    defaults                   0       0

```

---

### Post by Mustard on 2006-03-05
Hmmm..well that just makes it more of a mystery.  Everything looks perfect.

---

### Post by boichukj on 2006-03-05
I unplugged the firewire port and plugged in the usb 2.0 on the external drive and it will let me mount it as root but not as my user.  So how do i get it to work with my user the umask=0222 dosn't seem to do the trick.

---

### Post by gary1970 on 2006-04-04
I have a 8.4 gig Hard Drive that I have placed most of my music files over the past years . After installing ubuntu I have noticed that I can not find my 8.4 gig hard drive . Does anyone have any good ideas what I should do so that ubuntu sees the hard drive . Thanks for everyones time . ](*,) ](*,)

---

