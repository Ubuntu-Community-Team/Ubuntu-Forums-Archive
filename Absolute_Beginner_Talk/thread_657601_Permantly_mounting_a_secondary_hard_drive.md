---
title: "Permantly mounting a secondary hard drive"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-03
OK. Well let me say that I have used the gnome partition editor and I edited my hard drive to an ext3 file system. 
What I would like to do is to permanently mount the secondary drive so that when the system boots up I can click on the music folder in places and it accesses all of my music files that will be located on the secondary drive.
Where I am at is my drive is formatted but the only accessible user is root. I also cannot create any new folders or even change permissions when I click on the properties tab.
I have asked about this before but I keep getting commands like 

sudo mkdir /storage
sudo cp etc/fctd

but I have two drives. How do I know which drive I am affecting? Is there a way to do all of this through the GUI. I am trying very hard to learn linux but this is very opaque. Plus I am very worried about completely messing up my system because I have to use sudo all the time. If anyone is willing to be patient with me and work step by step I would appreciate it. Thanks in advance,

---

### Post by taurus on 2008-01-03
Is your second harddrive /dev/hdb1 or /dev/sdb1?  Open a terminal and post the output of this command here?  Also, where you do plan to mount it to, maybe /media/share?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

p.s.  What is your logging name since you need to change the ownership of that new mount point from root to your log in name so you can write to it.

---

### Post by mrphud on 2008-01-03
How do I cut and paste in bash? I can tell you that the secondary drive is /dev/sdb1 and is an ext3 filesystem. I am a soaking wet noob so I don't know how to paste the output.

My login name is jordan

---

### Post by taurus on 2008-01-03
Cut with the left button of your mouse and paste with the middle track ball.  Otherwise, cut with both left and right buttons holding down at the same time.

Anyway, you need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/share   ext3   defaults   0   1
```
Save it and close the gedit window.  Then, create a new mount point and mount it.

```
sudo mkdir /media/share
sudo mount -a
df -h
```
You should see your /dev/sdb1 mounted to /media/share.

Now, if you want to write to /media/share (you access your /dev/sdb1 by /media/share), you need to change the ownership of that mount point from root to your login name, jordan.  

```
sudo chown -R **jordan**:**jordan** /media/share
ls -la /media
```

---

### Post by mrphud on 2008-01-03
Code:

/dev/sdb1   /media/share   ext3   defaults   0   1

If I may ask what am I doing here? Is this saying what I would like to call the file?

second I created a back up of the fstab file just in case. When I work with sudo am I storing these things on the main hard drive?

also what is the difference between gksudo and sudo? I see them going back and forth. 

Thank you


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01520151

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x038f7af1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
```
This is the fdisk output.

---

### Post by taurus on 2008-01-03
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ByteJuggler on 2008-01-03
"sudo" stands for "super user do"  It means that whatever command follows is run as the super user e.g. with full administrative privileges.  It doesn't neccesarily pertain to a particular drive/partition only.  The files you're editing here however, yes, is all on the root partition

sudo is meant for use in a command-line/terminal window. 

gksudo is meant for use with GUI Gnome desktop applications, and pops up a GUI windows asking for a password instead.

The fstab line is defining to the system how it should mount your other drive at boot time, and where.  The first bit says which device to mount (/dev/sdb1), the second bit says where to mount it (/media/share), the third bit says what filesystem type to mount it as (ext3), the fourth bit specifies mount options to use (defaults) and the last 2 bits have to do with marking filesystems relevant to the "dump" command and the priority order for filesystem checking. (the root filesystem should be 1, with others ideally following with lower numbers, although having 1 as well wont hurt.)

---

### Post by derkaderka on 2008-01-04
hello, Im a new linux user, but Ive been pickin stuff up pretty quickly.  Ive been trying to mount my former external hard drive as an internal, and this is the most usefull thread i have found so far.

Heres my dilemma: i cant seem to get the hard drive mounted, no matter what ive tried.

the 250 gig hard drive is the one im trying to mount, the 120 is what im running ubuntu 7.10 from.  the 512MB is just an old usb flash drive, nothing to be concerned with.  Ive managed to get /etc/fstab edited to contain /dev/hda1 (thank you taurus!) but when i run the mount commands, it wont recognize the external, telling me that i have the wrong filetype, or the the table is unreadable.  I think the problem is that the 250 GB HD is an IDE fat32 system, and yet it wont let me specify that in /etc/fstab, always recommending vfat.  how should i classify it, and are there any other changes I need to make?

```
**derkaderka@LinuxBox:~$ sudo fdisk -l**

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14242   114398833+  83  Linux
/dev/sda2           14243       14593     2819407+   5  Extended
/dev/sda5           14243       14593     2819376   82  Linux swap / Solaris

Disk /dev/sdf: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000
```

```
**derkaderka@LinuxBox:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=66f5d7ea-46a8-47d6-b183-5c94d2bdfe49 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e0dc7703-3568-4702-a25c-f348896a41cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda1       /media/p0rnbox  vfat    defaults        0       1
```

```
**derkaderka@LinuxBox:~$ sudo mount -a**
mount: /dev/hda1: can't read superblock
```

---

### Post by taurus on 2008-01-04
If you don't have gparted, install it from synaptic.  Then, fire it up, System -> Administration, and see what does it say about your /dev/hda1.  Are there files on /dev/hda1?

---

### Post by ByteJuggler on 2008-01-04
> **derkaderka said:**
> ... I think the problem is that the 250 GB HD is an IDE fat32 system, and yet it wont let me specify that in /etc/fstab, always recommending vfat.  how should i classify it, and are there any other changes I need to make? ...

Just to clarify -- vfat == fat32.  Therefore, if you have a FAT32 partition, you are meant to use "vfat" as fs type.  I don't see anything wrong with that fstab line, does the mountpoint exist, and is the filesystem on the 120GB disk in good working order (Can you see it from Windows?)

---

### Post by derkaderka on 2008-01-04
> If you don't have gparted, install it from synaptic. Then, fire it up, System -> Administration, and see what does it say about your /dev/hda1. Are there files on /dev/hda1?

I do have files on the hard drive, if that what you mean.  as for the actual file /dev/hda1, it says its 0 bytes in size and is listed as "x-special/device-block".  I would like to avoid reformatting the 250gb drive if possible.

GParted wont work for me.  once i open it, it just hangs with the status message "scanning all devices..." at 100% CPU usage.  after an hour i gave up on it.  is there something else i can use?

> Just to clarify -- vfat == fat32. Therefore, if you have a FAT32 partition, you are meant to use "vfat" as fs type. I don't see anything wrong with that fstab line, does the mountpoint exist, and is the filesystem on the 120GB disk in good working order (Can you see it from Windows?)

the 120gig system works fine, however i never used it with windows.  thats the one i have ubuntu running off of, and im trying to add in the 250 as a secondary drive for storage.  it was originally a WD external.  yes /media/p0rnbox exists, but is there something special i need to do to make it a mount point?  all i did was create it with **sudo mkdir /media/p0rnbox**

---

### Post by dcstar on 2008-01-05
> **mrphud said:**
> OK. Well let me say that I have used the gnome partition editor and I edited my hard drive to an ext3 file system. 
What I would like to do is to permanently mount the secondary drive so that when the system boots up I can click on the music folder in places and it accesses all of my music files that will be located on the secondary drive.
.........
but I have two drives. How do I know which drive I am affecting?** Is there a way to do all of this through the GUI.**
......

Yes, despite all the people who tell you to stuff around with manual editing of files, there is an easy way to install a GUI tool to achieve exactly what you (and most beginners) want:

[http://ubuntuforums.org/showthread.php?t=654825&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=654825&highlight=pysdm)

---

### Post by derkaderka on 2008-01-05
> **dcstar said:**
> Yes, despite all the people who tell you to stuff around with manual editing of files, there is an easy way to install a GUI tool to achieve exactly what you (and most beginners) want:

[http://ubuntuforums.org/showthread.php?t=654825&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=654825&highlight=pysdm)

i have followed this through.  i can see the 250 gig from storage device manager, and i can fiddle around with the device config options, but the drive will stoll not mount.  i dont get any errors, simply nothing happens when i click the mount button, and it doesnt change to an unmount button like with other devices (i tested it with my usb flash drive, works fine with that)

im beginning to think that i will have to reformat my harddrive to make this work.  it seems like the problem is some kind of critical file corruption on the drive.  is there a way to check for file integrity on the drive, and possibly fix that?

---

