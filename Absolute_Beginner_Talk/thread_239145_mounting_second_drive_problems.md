---
title: "mounting second drive problems"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2006-08-18
Hello all,

I've installed a new 250GB HD to my 5 years old computer and I don't know why I can't mounting it.

I uses Gnome Partition Editor to format the new drive with ext3 FS.  I added it to the fstab file then run the following command:

sudo mount -a

AND I got the following Error.

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Not sure why.... (I am wondering if my motherboard does not support 250GB HD. but, Bios see it, Ubuntu see it.)

help... please.

Thanks,
Khanh

---

### Post by catlett on 2006-08-18
Post the ouput of these 2 commands
```
sudo fdisk -l
```
```
cat /etc/fstab
```

---

### Post by kpham.p on 2006-08-18
fdisk -l :
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2            1217        1459     1951897+  82  Linux swap / Solaris
/dev/hda3            1460        9729    66428775   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001   83  Linux


cat /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1       /home/kpham/Desktop/slave ext3 default  0       0


thanks,
khanh

---

### Post by catlett on 2006-08-18
Your /etc/fstab matches your partition. Try a couple of things. First double check that it is formatted to ext3 and not ext2 (it happened to me once with gparted) Go to System<Administration<Disks. Select the drive and see if it says extended 3.
The other thing to try is mounting it manually. Enter this command
```
sudo mount /dev/hdb1 -t ext3 /home/kpham/Desktop/slave
```

If you get the same error as earlier try it with auto detection of the filesystem ```
sudo mount /dev/hdb1 -t auto /home/kpham/Desktop/slave
```

If you still get errors, I would try formatting it again. Install gparted if you haven't
```
sudo apt-get install gparted 
```
Then go to System<Administration<Gnome Parttition Editor to access gparted. Run another format and try again. This might be the issue because the drive is operational, bios sees it, ubuntu sees it and your /etc/fstab is correct. If you get errors from above, I would think the format had issues.

But try trouble shooting with the above first

---

### Post by kpham.p on 2006-08-18
When mounting manualy as you shows it works. :) thanks.

> sudo mount /dev/hdb1 -t ext3 /home/kpham/Desktop/slave

I guess if I reboot the machine it should work? or what else should I do?

thanks,
Khanh

---

### Post by catlett on 2006-08-18
Well this is the issue. That command mounts the drive for a single session. When you reboot it will not be mounted. /etc/fstab handles mounting at boot. What we just did was issue the mount command for a session.
Try rebooting and see if /etc/fstab works and mounts. If it doesn't, issue the mount command again. If it doesn't have errors and mounts successfully again, you can at least mount it manualy each session.
The confusing part is /etc/fstab should work because it is giving the same command. :-k 
Reboot and see what happens

---

### Post by kpham.p on 2006-08-18
I reboot the machine and it didn't mount.  I remounted it manually and it works again. 

One question though; after it mounted the drive how come the icon didn't change from the folder to the harddrive icon?

thanks
Khanh

---

### Post by catlett on 2006-08-18
I do not know exactly. It may be because it isn't mounted in media. I know drives mounted in the media folder get icons on the desktop.
Is the drive an icon when you go to Places/Computer?

For the heck of it, you can mount it in the media folder and see what it does, icon wise.

```
sudo umount /dev/hdb1 -t ext3 /home/kpham/Desktop/slave
```
```
sudo mkdir /media/slave
```
```
sudo mount /dev/hdb1 -t ext3 /media/slave
``` That will unmount it, make a folder slave in the media folder and then mount the drive there. Does it get an icon in Places/Computer od the desktop?

---

### Post by kpham.p on 2006-08-18
catlett;

thank you so much for helping me out. the problem is my faults.  I type the option (default) wrong in the fstab file.  I should have type "defaults" instead of "default".  man, one little character "s" killing me.

Sorry about that...I taking up your times.

thanks,
Khanh

---

### Post by catlett on 2006-08-18
No time helping someone is wasted. 
One thing about computers, they are unforgiving. They expect us to be as exact as they are. 
Good eyes though. I didn't see it but now that you mentioned it, I see it.
Take care.

---

