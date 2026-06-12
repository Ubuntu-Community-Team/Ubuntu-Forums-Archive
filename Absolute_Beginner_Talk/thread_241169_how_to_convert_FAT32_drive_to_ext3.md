---
title: "how to convert FAT32 drive to ext3 ?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by bombitmd on 2006-08-21
I just installed Ubuntu to dual boot with XP. It's running nicely. I would like to access my files from Linux, and vice versa.  How do I do that?

Currently, I only have the [COLOR="Red"]/home[/COLOR] directory where I store my Linux files.  In XP, I store them in drive [COLOR="Blue"]D[/COLOR] (partitioned from a single HD). Drive [COLOR="Blue"]D[/COLOR] is FAT 32 as recommended by people so Linux could read it, but as of now, I still don't know how to get to it.  Obviously, XP can't read [COLOR="Red"]/home[/COLOR].

So what should I do?  I see two approaches:
1. Maintain my partitions and drives, and find out how to access [COLOR="Blue"]D[/COLOR] from Linux and [COLOR="Red"]/home[/COLOR] from XP.  (I found the program that's supposed to enable XP to access ext3 but haven't installed it yet.) OR...

2. I could merge the [COLOR="Blue"]D[/COLOR] and [COLOR="Red"]/home[/COLOR] partitions and convert it to purely [COLOR="Red"]/home[/COLOR] and use that ext3 program to access it from XP. Problem is, [COLOR="Red"]**how can I combine then convert the FAT32 drive D with my ext3 /home directory?**[/COLOR]

Could it be as simple as using Partition Magic to convert FAT32 into ext3 then merge them?  Assume already that I'll empty both directories since they ARE empty. (I've just installed Ubuntu and XP, and I have Ubuntu 5.04 only, so there's no Gparted.) 

Help on this matter would be great. Thanks!

---

### Post by Greycloak on 2006-08-21
ext3 partitions are not readable from windows.  You should be able to access the fat32 partition, unfortunately I'm not entirely certain how to go about it.

---

### Post by nalmeth on 2006-08-22
Ubuntu can read and write fat32, and windows can read/write ext3 (you'll have to find an ext3 driver for windows).

To start, in a terminal run:
sudo fdisk -l

This will show us your partition table.

The file /etc/fstab controls mounting devices and their mount points.
To have the fat32 mount at boot time, we would add a line in /etc/fstab, and make a directory in /media for the mount point.

Please post back with the fdisk output so we can see what the partition is called.

EDIT:
Since I'm running short on time, here's what to do
```

sudo mkdir /media/stuff 
```
(this is the mount point)
```
sudo gedit /etc/fstab
```
add this line to the end:
```
/dev/hdxx	/stuff	vfat	defaults	0 0
```
replace the xx with whatever label the fat32 partition has

to mount the drive manually:
```
sudo mount /dev/hdxx /media/stuff
```

---

### Post by bombitmd on 2006-08-22
Thanks nalmeth!  Did exactly that and was able to access drive D:

However, how come it didn't save right? In Linux, I edited a document located in My Folders (drive D:) and saved it.  When I started XP and checked the same file, it hadn't changed.  How come?  (I'm able to access /home while in Windows using this ext3 driver thingy.)

---

### Post by Cryonic on 2006-08-22
XP *can* write to ext3, use this nifty tool:
[http://fs-driver.org](http://fs-driver.org)

---

### Post by nalmeth on 2006-08-22
> In Linux, I edited a document located in My Folders (drive D:smile: and saved it. When I started XP and checked the same file, it hadn't changed. How come? (I'm able to access /home while in Windows using this ext3 driver thingy.)
To clarify,
This was your fat32 partition, right? Not the NTFS?
And you didn't get any errors about permissions? The changes were just not made?

---

### Post by bodhi.zazen on 2006-08-22
> **bombitmd said:**
> Thanks nalmeth!  Did exactly that and was able to access drive D:

However, how come it didn't save right? In Linux, I edited a document located in My Folders (drive D:) and saved it.  When I started XP and checked the same file, it hadn't changed.  How come?  (I'm able to access /home while in Windows using this ext3 driver thingy.)

Probably a permissions problem.

Assuming your mount point is /media/stuff:
```

sudo chown root:users /media/stuff
sudo chmod 777 /media/stuff

If you are paranoid:
sudo chmod 660 /media/stuff
(may have permission problems in Windows with paranoid settings)
```

Now edit fstab and change
```
/dev/hdxx	/stuff	vfat	defaults	0 0
```
to
```
/dev/hdxx	/media/stuff	vfat	auto,users,rw	0 0
```

Note: Your FAT partition will now automatically mount when you boot Ubuntu and be located at /media/stuff

Last:
```
sudo umount /media/stuff
mount /media/stuff
```

NOTE NO sudo on the last command.

Note: /stuff is NOT THE SAME LOCATION as /media/stuff!!
**Your "missing" files may be in /stuff rather then /media/stuff.**

Make sure the /stuff (not /media/stuff) directory is empty.
If /stuff is not empty, move any files in /stuff to ~ (your home directory)
sudo rmdir /stuff
Mount /media/stuff
Move files from ~ to /media/stuff.

Your "missing" files may be in /stuff rather then /media/stuff.

---

