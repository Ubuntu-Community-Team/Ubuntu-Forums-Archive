---
title: "Duplicate UUIDs"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by dhopley on 2007-07-05
Dear Forum , 
Hi , newbie here with a dual booting Fiesty and Windows 98SE . After an attempt to name and use a Windows Firefox profile (/media/hda1/Applications Data/..... in Fiesty Firefox a duplicate UUID state seems to have occurred in Ubuntu with my Windows 'C' drive (previously Hda1) now being supplanted by the 'D' backup drive (previously Hdc1) and both as you see from a cut 'n paste from a blkid list sporting the same UUID , which by appearance should properly be for 'D' , Hdc1 only . /media/Hdc1/ is no longer shown on my start screen . Blkid follows :     
derek@ubuntu:/media$ blkid

/dev/hda1: UUID="0531-08E2" TYPE="vfat" 

/dev/hdb1: UUID="dc2c6514-3e9f-4d56-81dd-feb890083f3c" SEC_TYPE="ext2" TYPE="ext3" 

/dev/hdb2: UUID="5d6c681d-8b23-4a78-9810-4752f6fa036d" TYPE="swap" 

/dev/hdb3: UUID="087804c9-dce3-4996-82cb-023aed40f9b5" SEC_TYPE="ext2" TYPE="ext3" 

/dev/hdc1: UUID="0531-08E2" TYPE="vfat" 

/dev/hdc5: UUID="2324-12E4" TYPE="vfat" 

/dev/hdc6: SEC_TYPE="msdos" UUID="3F26-12E4" TYPE="vfat" 

/dev/hdc7: UUID="1A5A-12E7" TYPE="vfat"
Any ideas ? ,
Derek

---

### Post by coffeecat on 2007-07-05
UUIDs baffle me, but I noticed a quirk with blkid after I changed a couple of partitions. I wonder if this might be the problem. It was still presenting me with the 'old' UUIDs even though the reformatted partitions would have had different UUIDs. It seems that it writes the UUIDS to a cache file first time around and then serves that up when you run 'blkid' whatever the changed state of the hard disk(s). I got round that by removing the cache file but I can't remember the details. I'm sure 'man blkid' will help. :wink:

As an alternative, have a look in /dev/disk which will be renewed every time you boot up. There's a way of matching the UUIDs in there with partition numbers but I can't remember how either - apart from running blkid. Sorry. :(

**Edit:** I've just done an experiment. I'm in Gentoo atm but I'm sure blkid will be the same in Ubuntu. The cache file is /etc/blkid.tab, and there's also an /etc/blkid.tab.old. When you run blkid the date stamp on blkid.tab.old is updated but blkid.tab stays the same. :-k If you delete blkid.tab and blkid.tab.old, a new blkid.tab is generated when you run blkid.

---

### Post by mcduck on 2007-07-05
Try 'ls -la /dev/disk/by-uuid' instead of 'blkid'. If that gives you duplicate UUID's as well then there's definitely something strange going on...

---

### Post by coffeecat on 2007-07-05
> **mcduck said:**
> Try 'ls -la /dev/disk/by-uuid' instead of 'blkid'.

That was the way of matching UUIDs to partition numbers I couldn't remember. :lol: Thanks, **mcduck**.

---

### Post by dhopley on 2007-07-05
Dear McDuck , 
Hi , please find as follows :
derek@ubuntu:~/sc92031-2.6.4/src$ ls -la /dev/disk/by-uuid

total 0

drwxr-xr-x 2 root root 180 2007-07-05 13:46 .

drwxr-xr-x 5 root root 100 2007-07-05 14:45 ..

lrwxrwxrwx 1 root root  10 2007-07-05 13:46 0531-08E2 -> ../../hda1

lrwxrwxrwx 1 root root  10 2007-07-05 14:45 087804c9-dce3-4996-82cb-023aed40f9b5 -> ../../hdb3

lrwxrwxrwx 1 root root  10 2007-07-05 14:45 1A5A-12E7 -> ../../hdc7

lrwxrwxrwx 1 root root  10 2007-07-05 14:45 2324-12E4 -> ../../hdc5

lrwxrwxrwx 1 root root  10 2007-07-05 14:45 3F26-12E4 -> ../../hdc6

lrwxrwxrwx 1 root root  10 2007-07-05 14:45 5d6c681d-8b23-4a78-9810-4752f6fa036d -> ../../hdb2

lrwxrwxrwx 1 root root  10 2007-07-05 14:45 dc2c6514-3e9f-4d56-81dd-feb890083f3c -> ../../hdb1

derek@ubuntu:~/sc92031-2.6.4/src$ 

This certainly shows the current situation but see the /etc/fstab/
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/hdb1

UUID=dc2c6514-3e9f-4d56-81dd-feb890083f3c /               ext3    defaults,errors=remount-ro 0       1

# /dev/hdb3

UUID=087804c9-dce3-4996-82cb-023aed40f9b5 /home           ext3    defaults        0       2

# /dev/hda1

UUID=0531-08E2  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hdc1

UUID=0531-08E2  /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hdc5

UUID=2324-12E4  /media/hdc5     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hdc6

UUID=3F26-12E4  /media/hdc6     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hdc7

UUID=1A5A-12E7  /media/hdc7     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hdb2

UUID=5d6c681d-8b23-4a78-9810-4752f6fa036d none            swap    sw              0       0

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0  

and also the /etc/mtab/

/dev/hdb1 / ext3 rw,errors=remount-ro 0 0

proc /proc proc rw,noexec,nosuid,nodev 0 0

/sys /sys sysfs rw,noexec,nosuid,nodev 0 0

varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0

varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0

procbususb /proc/bus/usb usbfs rw 0 0

udev /dev tmpfs rw,mode=0755 0 0

devshm /dev/shm tmpfs rw 0 0

devpts /dev/pts devpts rw,gid=5,mode=620 0 0

lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0

/dev/hdb3 /home ext3 rw 0 0

/dev/hda1 /media/hda1 vfat rw,utf8,umask=007,gid=46 0 0

/dev/hda1 /media/hdc1 vfat rw,utf8,umask=007,gid=46 0 0

/dev/hdc5 /media/hdc5 vfat rw,utf8,umask=007,gid=46 0 0

/dev/hdc6 /media/hdc6 vfat rw,utf8,umask=007,gid=46 0 0

/dev/hdc7 /media/hdc7 vfat rw,utf8,umask=007,gid=46 0 0

binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

which I have tried to edit to change the second /dev/hda1 entry to /dev/hdc1 only to see it overwritten in the next boot . Thanks for your attention McDuck and Coffeecat , are there Linux commands to patch these disk volume entries ?
Derek

---

### Post by bodhi.zazen on 2007-07-05
I do not know how to set a ID number on a fat partition (try gparted ?) or why your fstab is reverting to uuid after you set /dev/hdxy

I have some links for information on UUID for those who are interested.

[http://manual.sidux.com/en/part-uuid-en.htm](http://manual.sidux.com/en/part-uuid-en.htm)

[http://wiki.archlinux.org/index.php/Persistent_block_device_naming](http://wiki.archlinux.org/index.php/Persistent_block_device_naming)

+1 Arch Linux

---

### Post by dhopley on 2007-07-05
Dear Gentlemen ,
Mystery solved ! Looking at the two HDDs in MS-DOS the Volume labels were the same . To celebrate my plan to move to Ubuntu l'd bought a newer version of Norton Ghost for backup purposes , which claims to be able to backup EXT3 partitions , but this newer Ghost 2003 has additional switches , one of which supports by default copying of boot records etc. , obviously including the volume label . As I planned to try and integrate the two Firefoxes I'd  first backed up the Windows 98SE and unwittingly used this switch , and so messed up the Ubuntu boot up . After a reformat of the backup drive and a less enthusiastic backing up of “C” , Ubuntu now shows just the “C” , Hda1 drive and laments the non existence of Hdc1,2,3 & 4 , and I guess I'll have to rerun GRUB or even the full Alternate Install CD to clear that up . Thank you for your attention ,   
Derek

---

### Post by bodhi.zazen on 2007-07-05
I know norton ghost is popular, but there are some nice Linux tools as well :

1.  GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

Clonezilla : [http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/)

Download : [http://gparted.free.fr/GParted-Clonezilla/](http://gparted.free.fr/GParted-Clonezilla/)

2. Partimage : [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

3. g4u (ghost for unix) [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

