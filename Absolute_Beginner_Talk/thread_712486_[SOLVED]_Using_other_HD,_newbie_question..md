---
title: "[SOLVED] Using other HD, newbie question."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by ah pook on 2008-03-01
Please be kind. 
I have Gutsy running fine on a 120g IDE drive. this is /hdb. I also have an 80g SATA drive, with nothing on it, which is /sda. How do I make /sda available all the time to the system, so I can just drag movies and music over, in other words make it just another drive? I don't want to have to mount the drive every time, and also I'm having problems withpermissions and such, which I don't understand.

thanks in advance for any help...

---

### Post by Rocket2DMn on 2008-03-01
Can you post the output of thses commands:
```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by ah pook on 2008-03-01
geo@geo-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/hdb1
UUID=72e19d48-8940-4695-9599-16c4192f19ff  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/hdb5
UUID=51e1c2c6-7850-46bc-8770-4e8637fdea05  none            swap         sw                          0  0  
/dev/hda                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sda5                                  /media/sda5     swap         users,sw,user               0  0  
geo@geo-desktop:~$ sudo fdisk -l
[sudo] password for geo:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        9729    78148161    5  Extended
/dev/sda5               1        4612    37037857+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b081b07

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       13995   112414806   83  Linux
/dev/hdb2           13996       14593     4803435    5  Extended
/dev/hdb5           13996       14593     4803403+  82  Linux swap / Solaris
geo@geo-desktop:~$

---

### Post by Rocket2DMn on 2008-03-01
Why is there swap on the sda drive, did it have linux installed on it?  If you want to just flat out format it with plain ext3, download gparted
```
sudo apt-get install gparted
```
Then you can run it from System->Administration->Partition Editor.  Select the sda drive, format it clean with ext3 (or another filesystem of your preference).  Do what you're going to do to get it setup, then we'll add it to fstab.  Just post the fdisk output again and I'll show you how to add it to fstab.

---

### Post by Duck2006 on 2008-03-01
This may help with mounting the drive.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by ah pook on 2008-03-01
geo@geo-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        9729    78148161    5  Extended
/dev/sda5               1        9729    78148129+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b081b07

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       13995   112414806   83  Linux
/dev/hdb2           13996       14593     4803435    5  Extended
/dev/hdb5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by Rocket2DMn on 2008-03-01
OK.... I'm not sure why the swap is still there, did you try deleting the sda5 partition?  We'll add sda2 to your fstab.  
```
gksudo gedit /etc/fstab
```
Add the following line:
```
/dev/sda2 /media/sda2 ext3 defaults 0 0
```
save and close.

Then run the following commands:
```
sudo mkdir /media/sda2
sudo mount -a
sudo chown -R [yourusername] /media/sda2
```
If it says the directory already exists, that's ok, just proceed.  Please post any errors you get.  After running those commands, you should be able to read/write the drive which will be mounted at /media/sda2

---

### Post by ah pook on 2008-03-01
i was getting rid of sda5. do i need to edit that out of fstab?

---

### Post by Rocket2DMn on 2008-03-01
Yeah, you should get it out of fstab since you have hdb5 as your swap.

---

### Post by ah pook on 2008-03-01
ok now i'm getting this:
geo@geo-desktop:~$ sudo mount -a
mount: special device /dev/sda2 does not exist

any ideas?

---

### Post by ah pook on 2008-03-01
I nned to make a logical partition, right? with ext3?

---

### Post by Rocket2DMn on 2008-03-01
You don't need to make any logical partitions, you can have up to 3 or 4 regular partitions on a drive, and you don't even have to deal with partitions being logical unless you setup RAID I think.
Using GParted just delete all the partitions on the drive (make sure it's the correct drive!!!), then format all the space with 1 ext3 partition (or other filesystem of your preference).  Then run
```
sudo fdisk -l
``` to see what device is formatted with ext3 on sda (there should be only one).  Change my previous post's "sda2" to whichever is there (sda1...?).

---

