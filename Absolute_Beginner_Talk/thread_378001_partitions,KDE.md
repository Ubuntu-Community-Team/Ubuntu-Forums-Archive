---
title: "partitions,KDE"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Albert E. on 2007-03-06
Hi there!

I  a TOTAL newb needing help : Ive just installed ubuntu 6.10 on my laptop and i think i cant use the file system. I made 4 partitions: one for the already installed Windows,one fat32 for both OSs,one for ubuntu and the swap partition. The problem is that i can only see the Linux partition. I have seen on other laptops with linux that the windows partition is readable,and the fat32 should be visible too,right?

So my question is:
 Am i just not understanding  the filesys or did i do something wrong during the partitioning?
If I have missed to do something (like mount something perhaps?) can it be done at that stage or do i need to go through the whole installation process again?

Oh,one more thing: i was never asked if i wanted Gnome or KDE.Is there a way to choose one?

Thanks a lot!

---

### Post by ewankho on 2007-03-07
I think you need to mount them, see your fstab file if the windows partition are included.
Ubuntu by default uses Gnome, you can install KDE by installing KDE packages or installing Kubuntu instead.

---

### Post by Albert E. on 2007-03-07
oookey,
that helped! i was beginning to get desperate

Now what is a fstab file and where do i find it?

;)

---

### Post by Big_Croc7 on 2007-03-07
fstab is a file that lives in the /etc directory and contains information about which partitions are mounted when the system starts - you can edit it by typing

```

sudo cp /etc/fstab /etc/fstab.backup1
gksudo gedit /etc/fstab

```

The first line makes a backup copy (important in case you change something and make a mistake) and the second line opens it in gedit ('sudo' means 'do this command with system-level access rights'; gksudo is the same but for graphical programs).

Are you running dapper or edgy?

If dapper, you should see something like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               xfs     defaults        0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

You want to add similar lines for the other partitions.  Can you type fdisk -l /dev/hda (in a terminal) and copy the output to here?


Also, if you want to install KDE, try the package kubuntu-desktop through synaptic (this installs KDE itself, plus other applications for the KDE environment).

EDIT: you need to run fdisk as root - so the command will be ```
sudo fdisk -l /dev/hda
```
(Note: that's a lower-case L after fdisk.)

---

### Post by Albert E. on 2007-03-07
thanks for the help!

I think i'm using edgy

that's  what the fstab file contains:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2df076fe-1c31-41c1-8dbd-d5db10563573 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=7aa0c260-652c-4f4a-ac83-63eba595b676 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

as far as i understand it, i only have my linux(/dev/sda3) and my swap partition(/dev/sda4) there

i ran 'sudo fdisc -l /dev/sda' and got:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        5222    20972857+   b  W95 FAT32
/dev/sda3            5223        7249    16281877+  83  Linux
/dev/sda4            7250        7296      377527+  82  Linux swap / Solaris


why is there a * only for the windows partition? shouldn't there be for the linux too?
yep, and how do i and sda1 and sda2 to that fstab file?

and thanks a lot again! life is so much better when someone help with such things!

---

### Post by Big_Croc7 on 2007-03-08
No worries! Glad I can help :-)

To answer the last question first: the Windows bootloader can only boot into partitions that have a special flag set at the beginning of the partition (the boot flag); however, Ubuntu dosen't need that; a file called menu.lst tells Grub were to find the linux kernel, and it dosen't care about the 'boot' flag at all.

Righty-ho:

First of all, you need to choose and create a mount point for your partitions; this will be the access path for that partition.  Many people like to keep all mounted partitions in /media, though I don't necessarily.  You could chose /data and /windows, for example, or /media/data and /media/windows, or something else.  I'll assume you want your fat32 partition mounted in /data and your ntfs partition in /windows.

Make the directories:
```

sudo mkdir /data
sudo mkdir /windows

```

Make the data partition writable by all users (assuming that's what you want):
```

sudo chmod 777 /data
sudo chmod 777 /windows

```
('777' means read and write access for everyone)

Then add the following lines to your fstab:
```

/dev/sda2     /data    vfat    defaults   0   0
/dev/sda1     /data    ntfs    defaults,errors=remount-ro   0   0

```

reload your fstab file with 'sudo mount -a' and you should be good to go!

2 points however: firstly, you won't be able to write to the ntfs partition easily without additional work (though the Fat32 partition work be fine).  There are two things that determine whether you can write to a partition - the first is the permissions of the mount point (set by 777 etc, or by right clicking on the folder in Nautilus), and the second is the mount type for the filesystem; for ntfs, this will be read-only for all users without adding special tools for ntfs partitions.
Secondly, some people have reported problems with mixing /dev labels and UUID ones in fstab, but generally I think it works fine.

---

### Post by Albert E. on 2007-03-08
[B]ok,
 i edited the fstab to:[/B]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2df076fe-1c31-41c1-8dbd-d5db10563573 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=7aa0c260-652c-4f4a-ac83-63eba595b676 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2       /data           vfat    defaults           0       0
/dev/sda1       /windows        ntfs    defaults,errors=remount-ro  0  0
[B]
and got :[/B]
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**so what did i do wrong?** :confused:

---

### Post by Big_Croc7 on 2007-03-09
hmm...

did the other partition mount sucessfully?

The first thing to check is to see if you can mount it manually:
```

sudo mount /dev/sda2 /data 
```

If that works sucessfully, try replacing the line in fstab with
```
 /dev/sda2 /data vfat ro,users,exec,umask=000 0 0 
```

That tells it to mount read-only (the 'ro') with relaxed permissions; if that works and you can read your files, then try the same but with 'rw' instead.  If that dosen't work you can try typing dmesg | tail to see if there's anything useful there.

---

