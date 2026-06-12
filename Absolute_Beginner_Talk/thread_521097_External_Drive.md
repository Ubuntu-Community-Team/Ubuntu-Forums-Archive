---
title: "External Drive"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by manifresh006 on 2007-08-09
Ubuntu will not recognize the external hard drive

Is a Seagate 250G 3.5 IDE:)
Do I have to download a driver for it ? Or what could I do?:confused: 


I would really appreciate it if someone might help me.	\\:D/

---

### Post by Inxsible on 2007-08-09
post the output of the following 2 commands

```
cat /etc/fstab
``` ```
sudo fdisk -l
```-l is lowercase L

---

### Post by manifresh006 on 2007-08-09
Ok But then it told me this,

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux
/dev/sda2               1           1           0+  83  Linux
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by manifresh006 on 2007-08-09
Any more suggestions Mr.Inxsible

---

### Post by Inxsible on 2007-08-09
> **manifresh006 said:**
> Any more suggestions Mr.Inxsible
you still havent posted your fstab.

also make sure you connect the external Seagate drive and then do the fdisk command i gave you earlier.

---

### Post by manifresh006 on 2007-08-09
Sorry but what is the  fstab?:confused:

---

### Post by splintercellguy on 2007-08-09
Copy the output of cat /etc/fstab is what he wants you to do.

---

### Post by manifresh006 on 2007-08-09
I think is this?????

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d07a6ef7-f7da-491b-b556-4296b9ce4bd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4979686e-8f7a-46b2-931b-06fd2c25b5c7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by logos34 on 2007-08-09
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30401 244196001 83 Linux
**/dev/sda2 1 1 0+ 83 Linux**
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order

Strange entry--looks like sda2 may be a sliver of a partition at the front of the disk.  Can you detect it using Gparted?  The flag indicates sda1 is a bootable linux primary partition. (but there's no swap partitiion)

**sudo gparted**

click on the drop-down box upper right corner

You could try adding an entry for theexternal drive to fstab and see if it shows up on reboot.

Or just try

[B]sudo mkdir /media/sda1

sudo mount -t ext3 /dev/sda1 /media/sda1[/B]

---

### Post by manifresh006 on 2007-08-09
mannii2007@ubuntu:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
 
That what I got once I opened the Terminal and typed

**sudo mkdir /media/sda1**

---

### Post by logos34 on 2007-08-09
it already exists.  Now mount it there

---

### Post by Inxsible on 2007-08-09
> **manifresh006 said:**
> Ok But then it told me this,

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux
[COLOR=Red] /dev/sda2               1           1           0+  83  Linux
Partition 2 does not end on cylinder boundary.[/COLOR]

Partition table entries are not in disk order
I think there is something wrong with the way you created your partitions. Like already noted, the Linux partition seems too small to even hold the OS. But you are obviously running Ubuntu. (I hope you are not running on LiveCD to use the commands and suggestions given to you.)

---

### Post by logos34 on 2007-08-09
I assumed the OP was ruuning Ubuntu from the hda drive.  

I'm not sure what happened with the partitioning on sda.  Sda1 looks to be root (flagged bootable) and takes up the entire disk (1-30401).  sda2 seems like it was added after sda1 was created but maybe it's no loger there (or maybe just on the partition table only)

---

### Post by manifresh006 on 2007-08-09
Do you think it might be the EHD?
I just bought it..

---

### Post by logos34 on 2007-08-09
anything's possible.  What exactly is on this disk?

---

### Post by manifresh006 on 2007-08-10
Well lots of song about 40 movies or so and some fam pics...

O and No not runnin on  live cd 

It just doesn't pick it up Any other suggestions guys....:(

---

### Post by logos34 on 2007-08-10
Actually the system does pick it up (sort of)--fdisk sees it.

The mount point already exists.  If
**sudo mount -t ext3 /dev/sda1 /media/sda1**

doesn't work, try adding an entry in fstab and see if it mounts on reboot:
> 
/dev/sda1 /media/sda1 ext3 defaults 0 2

If that fails, try running a filesystem check on sda1:

**sudo fsck -f -v /dev/sda1**

---

### Post by Inxsible on 2007-08-10
If its an external drive, then you should mount it using pmount. Look at my signature for a link on how to use pmount.

---

### Post by manifresh006 on 2007-08-11
Okay but how do I know how to choose the #,letters and the s or h letter 

Tried a couple of combination but nothin.

---

### Post by manifresh006 on 2007-08-12
Well  I give up trying to save all the things I had in there how could I just reformat the External Hard Drive and make it work again.:confused:

---

### Post by manifresh006 on 2007-08-12
Well I downloaded this thing from seagate dot com called seatools for linux but don't understand it. talks about how formating the hard drive and all kinds of things.Of course that I don't get:(

---

### Post by undertakingyou on 2007-08-12
have you tried using pmount as previosly suggested?  Also I assume that this is a USB drive.  Sometime I have to plug it into a different port and then pmount takes over.

---

### Post by manifresh006 on 2007-08-13
Well decided to put an older version on to see what happened and the EHD did work on the Live CD 6.06 and installed it

But, Now I can't write in it here are some pics of what happen when I'm trying to put somthing in it
And when I tried to change the configuration of it...

[ATTACH]40546[/ATTACH]

[ATTACH]40547[/ATTACH]

[ATTACH]40548[/ATTACH]

---

### Post by manifresh006 on 2007-08-15
Any help again.:confused:

---

### Post by manifresh006 on 2007-08-15
Really need this EHD...:(

---

### Post by manifresh006 on 2007-08-16
come on anyone....:confused:

---

### Post by logos34 on 2007-08-16
sudo chown -R <username> /media/DELOSSANTOS

Does that help?

So you're tryinng to use this with Dapper now and you reformated sda1 as fat32 (vfat)?

---

### Post by manifresh006 on 2007-08-18
This would erase the hard drive "Re-Formatted"?

Or

Try to access the DH?

---

### Post by manifresh006 on 2007-08-18
This would erase the hard drive "Re-Formatted"?

Or

Try to access the DH?

---

### Post by manifresh006 on 2007-08-19
This command will Reformat or just erase? :confused::confused::confused::confused::confused:

---

