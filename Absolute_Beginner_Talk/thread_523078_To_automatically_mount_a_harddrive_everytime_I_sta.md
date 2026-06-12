---
title: "To automatically mount a harddrive everytime I start ubuntu, what must I do?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by chris_gpt on 2007-08-11
I've altered fstab

original file:
# /etc/fstab: static file system information
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc                    /proc              proc      defaults      0           0
dev/hda11            /                    ext3      defaults,errors=remount-ro  0      1
dev/hda12          none               swap    sw              0            0
/dev/hdc              /media/cdrom0  udf,iso9600 user,noauto   0         0

(to this I added 1 more line)

/dev/sda            /media/firewireDisk   ext2   auto,user,rw      0       1


Please note, I reformated the firewire disc using disk utility from OS 10.3.9 and selected the "unix format" (also not in 10.4.x they have two similar formats, "unix format" and "unix format (journaled)" I remember from one of Dr. Seyfarth's classes that the only difference between ext2 and ext3 was what MacOS calls a 'journal'.  My guess, NOT CERTAINTY that unix format is ext2 and unix format (journaled) is ext3.

NB: All I did was change fstab (and yes I did do:    sudo cp fstab fstab.old      before I altered fstab and the working directory was /etc).

I'm going to manually make the media/firewireDisk directory and see that helps but I have a nagging memory that I need to alter at least one more file, if not also change the newest line in fstab.

Thanks
-- Chris

---

### Post by BobCFC on 2007-08-11
I do not have a firewire drive but I do have an external USB hard drive.  Ubuntu automatically mounts this for me using hotplug if there is no reference to the device in /etc/fstab.  I found that adding an entry for the device actually interferes with the hotplug.   

Maybe firewire is different.

I would first practice mounting the device by hand, then it should be easy to translate this into an fstab entry.
[COLOR="Red"]
I notice that you are trying to mount /dev/sda  which refers to the whole drive.  You want the first partion such as **/dev/sda1**[/COLOR]

To see the devices and their files systems type  **sudo fdisk -l** (l for Larry the lamb)  

Then you can try **sudo mount -t ext3 /dev/sda1 /media/firewireDis**k or whatever to mount it manualy without rebooting.

---

### Post by chris_gpt on 2007-08-11
That didn't work.
How do I find out what file structure on this disk is?

I typed      sudo mount -t FILETYPE /dev/sda1 /media/frewireDisk

where FILETYPE was ext, ext2, ext3, ufs, and about 4 other file types (all of which gave the error list below).

The errors on the mount is the following

mount:  wrong fs type, bad option, bad superblock on dev/sda1, missing codepage or other error
              In some cases uses info is found in syslog - try
              dmesg | tail or so

Thanks,
-- Chris

---

### Post by BobCFC on 2007-08-11
I can only think of a command that shows you the type of currently mounted filesystems off the top of my head.

If you install gparted it should be able to identify the most common ones.  It will also let you right click on a partition and reformat it to another type.  If there is no data on there to worry about.

```

sudo apt-get install gparted
```


Then you can find it on the System->Admin menu I think.  Remember you can only manipulate an unmounted partition.

---

### Post by Paul133 on 2007-08-11
I'm pretty sure Linux format is the journalled ext3. I know I have my filesystem is ext3.

---

### Post by chris_gpt on 2007-08-12
Thanks, bob, but I've got over 6 gigs on it and I want to use the external HD for *both* MacOS10.3.9, 10.4.9 and ubuntu (I have two laptops only one with a motorolla-built processor and it's my "deuce" system that Linux and Mac OS 10.3 on it).

BTW no internet on my *second* system.  I thought get-apt was a command that required an internet connection to work properly.  

Thanks all your help.

reminder, external disk has "unix format" (i.e. *not* journaled).

I might wind up hooking the external HD into the computer I'm on and just make it a format I know the name of in mount and all OSes I have can use.  I know that I can't use HFS (unless I go through and change over 2000 file names so their short enough), can ubuntu 6.0.6 handle HFS+?  Last I looked (maybe 2 years ago), no linux could handle HFS+.

Thanks
-- Chris

---

### Post by chris_gpt on 2007-08-12
BTW:
Thanks everyone who's responded

---

### Post by schorsch on 2007-08-12
I guess Ubuntu is able to mount HFS+ partitions. It is not mentioned in the manpage of the mount command but there is kernel module in kernel 2.6.16-20:

```
grep hfs /lib/modules/2.6.20-16-generic/modules.dep 
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/squashfs/squashfs.ko:
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_hfsc.ko:
/lib/modules/2.6.20-16-generic/kernel/fs/hfsplus/[COLOR="Red"]hfsplus[/COLOR].ko:
/lib/modules/2.6.20-16-generic/kernel/fs/hfs/hfs.ko:
```

---

