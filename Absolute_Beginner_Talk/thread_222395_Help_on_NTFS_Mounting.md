---
title: "Help on NTFS Mounting"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Prosis on 2006-07-24
Hello,

I am aware that this must be a popular question and I apologize.  I have followed the instructions found at [http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support) to activate the support of my NTFS hard drive.  Now I don't know where to access it.

Also, there are folders available in the /tmp directory that match my hard drives but they are in read only and even as sudo bash or sudo su I can't change the permissions.

Finally, in the My Computer available under Shortcut menu on the top, I can see all 3 of my NTFS partition but cannot access any of them

Can anyone tell me how to go about this problem?

Thanks!

---

### Post by aysiu on 2006-07-24
Can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Just copy and paste those three separate commands into the terminal. Then highlight everything in the terminal and copy and paste it back here.

---

### Post by Prosis on 2006-07-25
Sorry that some words are french, my Ubuntu is french.  I translated most of the words but since I was not sure of the exact terminology when referring to hard drives, I left some untranslated.

```
Disc /dev/hda: 163.9 Gb, 163928604672 bytes
255 heads, 63 sectors/pistes, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Périphérique Amorce Start         End       Blocks  Id  System
/dev/hda1               1        6434    51681073+   7  HPFS/NTFS
/dev/hda2            6435       13502    56773710    7  HPFS/NTFS
/dev/hda3   *       13503       19741    50114767+  83  Linux
/dev/hda4           19742       19929     1510110    5  Extended
/dev/hda5           19742       19929     1510078+  82  Linux swap / Solaris

Disc /dev/hdb: 20.0 Go, 20020396032 bytes
255 heads, 63 sectors/pistes, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Périphérique Amorce    Start      End      Blocks    Id    System
/dev/hdb1   *           1        2434    19551073+   7  HPFS/NTFS


FileSystem            Tail. User Avail. %Used. Mounted on
/dev/hda3              48G  2,6G   43G   6% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4,0K  252M   1% /var/lock
udev                  252M  160K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-26-386/volatile
/dev/hdb1              19G  9,0G  9,7G  49% /tmp/disks-conf-hdb1
/dev/hda2              55G   18G   37G  34% /tmp/disks-conf-hda2


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/hda1 ntfs-fuse auto,gid=1001,umask=0002 0 0
```

---

### Post by aysiu on 2006-07-25
Okay, follow these instructions in exactly this order: ```
sudo umount /dev/hda2
sudo umount /dev/hdb1
sudo mkdir /media/hda2
sudo mkdir /media/hdb1
sudo nano -B /etc/fstab
``` This will open up your /etc/fstab file in a text editor. Paste in these two lines at the end of the file: ```
/dev/hdb1 /media/hdb1 ntfs nls=utf8,umask=0222 0 0
/dev/hda2 /media/hda2 ntfs nls=utf8,umask=0222 0 0
``` Then to save, press Control-X, Y, and Enter, in that order. Finally remount your drives: ```
sudo mount -a
```

---

### Post by Prosis on 2006-07-25
Worked fine, now all I have to do is create shortcuts to them!

I'll have to do the same with hda1 too I guess (which is not my Linux partition it's my master Windows partition)

Thanks a lot! :)

Oh but why can't I write in them and is it possible to do so? (in graphic mode as much as possible)

---

### Post by aysiu on 2006-07-25
NTFS is read-only from Linux. I noticed you had a FUSE line in there. I'm not sure how stable FUSE is these days.

---

### Post by Prosis on 2006-07-25
Oh well,if I intend on crossing over to Linux, I shouldn't need NTFS anymore...

Thanks! :)

---

### Post by mejohnsn on 2006-07-26
Although the 'mount' output calls the partition types 'rw', the built-in
ntfs support for Dapper 6.06 is really read only. When the kernel was released, there were still too many problems with NTFS support to make this read/write. These problems are not the fault of anyone on the Linux teams: it is because Microsoft keeps the technical details of NTFS secret, so that the dedicated teams have had to reverse-engineer NTFS!

There are several options for read/write, perhaps when Ayisu gets back to this thread, he can tell you which is best. I haven't made up my mind yet. The common options are "mount.captive-ntfs" and "ntfs-3g". There are also "ntfsmount", with its counter-intuitive UI, and "mount.ntfs-fuse", which at least are on the Dapper CD.

---

