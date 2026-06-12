---
title: "Spare Hard Drive"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Gazz777 on 2007-12-05
Hi, I have just added Ubuntu, and I boot up and asked either Windows or Ubuntu, :KS

Looks great and given some time I think this will be my primary OS, I like the feel of it.

As you would expect my PC was geared for Windows and has been for years,:(  

I have a spare 320gig drive that I hold most of my music in, I am almost sure when I formatted the Disc after installation I used NTFC and not Fat32.

I notice Ubuntu doesn't see the H/Drive, :confused:

Is it possible to share this drive with both Windows & Ubuntu without partitioning the drive, 

I have years of Music and no way do I want to lose this, if it isn't possible then ok I can still use Windows to play music, 

err I think I have about 30gig left free on H/Drive.

Thanx in advance.

Regards
Gary  :)
:guitar:

---

### Post by forestpixie on 2007-12-05
can you do the following in a terminal and paste the results here, (applications > accessories) - just in case you don't know for the first one it'll ask for a password, put your password in - it won't show but it's there

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by candtalan on 2007-12-05
'I have years of Music and no way do I want to lose this'

I trust that you have a serious backup of this data? I had two hard drives fail, both within warranty period. 
Backup of data is also relevant at this stage more than ever because you are starting out on a real new adventure - open source!  :-)  When I started I soon got curious, and a bit ambitious. Linux is safer than windows at user level. However, once you put your password in to escalate to root privilidges, you have a *lot* of power, and, when I did this, I did not have much experience. I found my curiosity and ambitions soon helped me screw up big time. :-( 
 But  - I did have ok backups :-)

---

### Post by hyper_ch on 2007-12-05
Backups are always good advice ;)

You can add read and write support for ntfs within linux.

---

### Post by Gazz777 on 2007-12-07
[can you do the following in a terminal and paste the results here, (applications > accessories) - just in case you don't know for the first one it'll ask for a password, put your password in - it won't show but it's there

```
sudo fdisk -l
```

```
cat /etc/fstab
```[/QUOTE]

gary@Linuk-DeskTop:~$ sudo fdisk -l
[sudo] 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1afa1af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38912   210162330    f  W95 Ext'd (LBA)
/dev/sda5           12749       16152    27342598+  83  Linux
/dev/sda6           16573       38912   179446018+   7  HPFS/NTFS
/dev/sda7           16153       16572     3373618+  82  Linux swap / Solaris

Partition table entries are not in disk order
gary@Linuk-DeskTop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=84e97a57-af0d-498f-9002-0da15958fbf1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8E546B64546B4E51 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=5288979288977369 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=49179bb9-d6f3-46cb-a87f-c177eb1c93c1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
gary@Linuk-DeskTop:~$ 


any help, thanx :(

---

