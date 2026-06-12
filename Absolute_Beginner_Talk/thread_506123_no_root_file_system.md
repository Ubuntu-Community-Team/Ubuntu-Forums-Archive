---
title: "no root file system"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by wak_maximus on 2007-07-21
i want to install Ubuntu on my machine..
however, during partitioning, i facing a problem "no root file system is defined"..
what is that mean??

and here is my partitioning plan:

device           type     mount p.        size         used space
dev/sda
   dev/sda1     ntfs   /media/sda1   21459MB     14400MB
   free space                               9993MB
   dev/sda5     ext3   /media/sda5  8562MB        306MB
   dev/sda7     ext3   /home/sda7  19362MB     unknown
   dev/sda6     swap                     641MB        unknown


what is file root system?
and how i can use my free space (9993MB) to put into home/sda7?

---

### Post by nitro_n2o on 2007-07-21
The root FS  "/" contains /boot /bin /etc / opt /var /lib /dev /tmp /media and some other things..  you'll have to have to install ubuntu .. 

If you r in the liveCD  using gparted just go  back and change your partition plan to mount /dev/sda7 as root

---

### Post by wak_maximus on 2007-07-21
during the installation process, i can re-partitioning my hard drive..
can i mount it using that??

i'm using Desktop CD...

---

### Post by Sef on 2007-07-21
[Live CD Install]("http://www.psychocats.net/ubuntu/installing") 

[Alternate cd install]("http://users.bigpond.net.au/hermanzone/")

---

### Post by wak_maximus on 2007-07-21
thanks..
the problem is just the mount name..
i change the "media/sda5" to "/"..
and it fixed...:)

---

### Post by wak_maximus on 2007-07-21
> **wak_maximus said:**
> i want to install Ubuntu on my machine..
however, during partitioning, i facing a problem "no root file system is defined"..
what is that mean??

and here is my partitioning plan:

device           type     mount p.        size         used space
dev/sda
   dev/sda1     ntfs   /media/sda1   21459MB     14400MB
   free space                               9993MB
   dev/sda5     ext3   /media/sda5  8562MB        306MB
   dev/sda7     ext3   /home/sda7  19362MB     unknown
   dev/sda6     swap                     641MB        unknown


how can i use my free space (9993MB)??
to be mount as ext3..

---

### Post by nitro_n2o on 2007-07-21
gparted will prompt you for the FS... you just select ext3

---

### Post by louieb on 2007-07-21
> **wak_maximus said:**
> how can i use my free space (9993MB)??
to be mount as ext3..
Depends on where the free space is. Or actually in you case. You should be able to use GParted and turn the free space into a primary partition. If not post a screen shot of the GParted window. Or to post your partition table [FONT=Fixedsys][SIZE=3]**use sudo fdisk -1  (lowercase L) .**[/SIZE][/FONT]

---

### Post by wak_maximus on 2007-07-21
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2609    20956761    7  HPFS/NTFS
/dev/sda2            3825        7297    27896872+   f  W95 Ext'd (LBA)
/dev/sda5            3825        4865     8361801   83  Linux
/dev/sda6            7220        7297      626503+  82  Linux swap / Solaris
/dev/sda7            4866        7219    18908473+  83  Linux

Partition table entry is not in order -->what does this mean??


during installation, on partitioning part, /dev/sda2 didn't come out..
and it shows that it have 20GB++..
i want it to be /dev/sda7..how to do that??

---

### Post by louieb on 2007-07-21
looks alright. First a little on your partitions
sda1 is a primary partition.
sda2 is an extended partition that is it does not contain data directly. It serves as a container for logical partitions sda5,sda6 and sda7. You do not directly use this partition. 
sda5,sda6 and sda7 are logical partitions that you can use. 
** Partition table entry is not in order **if you look at the start block column you will see sda7 come before sda6.  I see that a lot its nothing to worry about, it will work just fine that way. 

Did you install Gparted? Install it or run it of the live CD. its under system>admin. 
You should be able to click (right or left i forgot which) on the 9000+ MB unused space and turn it into a usable primary partition. Have you tried that yet? What happened? [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
Note due to the location of the unused space it can only be used as a primary partition.

---

