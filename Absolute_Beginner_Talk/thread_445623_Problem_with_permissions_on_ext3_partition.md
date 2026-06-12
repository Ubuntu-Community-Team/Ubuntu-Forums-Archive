---
title: "Problem with permissions on ext3 partition"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by The other One on 2007-05-16
Hey all,

I'm completely rapt with Ubuntu and am trying to make the final transitions from my existing XP install to make Ubuntu my primary OS. Last night I used GParted for the 1st time (not bad, Partition Magic is a little smoother, but it did the job) and created an ext3 partition on some free space on one of my HDDs with the intention of copying the media from My Documents in XP (Music, Pix and Videos), but I've hit a snag.

For some reason, I can't get write access to the new partition (sdb8 ). When I check it's properties, the owner is listed as unknown, and the partition is read only. I did a heap of searching here in the forums last night and tried sudo chown to my user name, but it hasn't worked at all.

Can anyone help with this? I'm really keen to come over from The Dark Side!

---

### Post by Najand on 2007-05-16
Can you copy and paste your /etc/fstab file here.

---

### Post by The other One on 2007-05-16
Yep, here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6 -- converted during upgrade to edgy
UUID=daabe9eb-b2e0-4d57-a045-f2b0f1cda6cc / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=D40856CB0856AC6C /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sdb7 -- converted during upgrade to edgy
UUID=46badb6c-2a12-475b-b46a-4886f2c9aa90 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

It seems odd to me that there's no reference to this partition in there

---

### Post by taurus on 2007-05-16
Can you post the output of these two commands from a terminal?

```
id
sudo fdisk -l
```

---

### Post by The other One on 2007-05-16
Sure, here they are.


```
dandness@dandness-desktop:~$ id
uid=1000(dandness) gid=1000(dandness) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(dandness)
dandness@dandness-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2        1271    10201243+   7  HPFS/NTFS
/dev/sdb6            1272        3821    20482843+  83  Linux
/dev/sdb7            3822        4083     2104483+  82  Linux swap / Solaris
/dev/sdb8            4084       23243   153902668+  83  Linux

```

---

### Post by taurus on 2007-05-16
Looks like /dev/sdb8 has not mounted at all.  Therefore, you need to mount it before you can access it.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb8   /media/sdb8   ext3   defaults   0   1
```
Save it.  Then, create a new mount point, mount it, and change the ownership /media/sdb8 from root to your login name, dandness.

```
sudo mkdir /media/sdb8
sudo mount -a
sudo chown -R dandness:dandness /media/sdb8
ls -la /media
```

---

### Post by The other One on 2007-05-17
Sweet, I'll give it a try when I get home.

Can you tell me how to interpret the outputs? I'm always keen to learn this stuff for myself rather than always asking a guru for the answers.
I'm guessing fstab is file system table, and that it's outputting the format of my mounted partitions, but what do the outputs of id and fdisk -l mean?

---

### Post by The other One on 2007-05-17
Brilliant! That worked perfectly - I'm now able to drag and drop the media from my NTFS partition to sdb8!

Thanks Najand and taurus!:biggrin:

---

### Post by southernman on 2007-06-06
*bows to tarus*

Thank you tarus!

---

