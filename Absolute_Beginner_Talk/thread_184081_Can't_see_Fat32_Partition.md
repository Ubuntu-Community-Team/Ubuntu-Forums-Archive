---
title: "Can't see Fat32 Partition"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by kokas on 2006-05-29
Hi there,

I have 5 partitions in my disk after installing Ubuntu. They where: Swap, Windows XP, one I made for the My Documents folder of XP, Backup and one for linux...
They where all NTFS folders except for the Linux and swap ones of course....since I had all my files ins the My Documents and Backup folders I wanted to made the acessible to read and writte in Ubuntu...I went to windows - partition Magic and formated (after moving everything to My Documents) the Backup Partition with the Fat32 file format....everything went ok and I can use it on windows bu it doesn't show up in Ubuntu....except that when I go to System > Administration > Disks....I can see it but it doesn't let me Enable it...

Any ideas ?

---

### Post by Sutekh on 2006-05-29
You need to read and follow the instructions in this link

[http://psychocats.net/ubuntu/mountwindows.php]("http://psychocats.net/ubuntu/mountwindows.php")

---

### Post by kokas on 2006-05-29
I did follow the instructions and it told me when I tried to mount this is what showed up:

[B]
nelson@nelson-desktop:~$ sudo mount -a
mount: /dev/hda5 already mounted or /backup_files busy
mount: according to mtab, /dev/hda5 is mounted on /media/hda5
mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

--------------------------------------------------------------------------------------------------
[B]GNU nano 1.3.10                            File: /etc/fstab                                                      Modified

/fat_files vfat iocharset=utf8,umask=000 0 0# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/B]

The partition I don't see is /dev/hda6

---

### Post by Sutekh on 2006-05-29
[quote=kokas][B]
nelson@nelson-desktop:~$ sudo mount -a
mount: /dev/hda5 already mounted or /backup_files busy[/B][B]

...


/dev/hda[COLOR=Red]5[/COLOR]       /media/hda[COLOR=Red]5[/COLOR]     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda[COLOR=Red]5[/COLOR]       /media/hda[COLOR=Blue]6     [/COLOR]ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda[COLOR=Blue]6[/COLOR]       /media/hda[COLOR=Green]7[/COLOR]     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
[/B][/quote] Just a typo i think

```
/dev/hda[COLOR=Red]5[/COLOR]       /media/hda[COLOR=Red]5[/COLOR]     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda[COLOR=Blue]6[/COLOR]       /media/hda[COLOR=Blue]6     [/COLOR]ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda[COLOR=Green]7[/COLOR]       /media/hda[COLOR=Green]7[/COLOR]     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

---

### Post by kokas on 2006-05-29
Yeah I found it weird also...but all I did was copy paste so maybe something is wrong

---

### Post by Sutekh on 2006-05-29
If you unmount the offending /dev/hda5
```
sudo umount /dev/hda5
```
then fix the fstab and remount it
```
sudo mount /dev/hda5
```
Do things resolve?

---

### Post by kokas on 2006-05-30
Ok I kind of fixe the fstab file and now it doesn't give me any error messages. I'm also able to acess the FAT32 partition I created trough a VFat I created in the root folder with the name Backup...I followed the instructions in the same page for the FAT32 partitions...
One thing I don't understand is why the partition is created has a Virtual Fat that shows only in the root folder instead of a Disk in the desktop like the other partitions. Or at least if I could create a shortcut in the desktop would be ok.

---

### Post by Ben Sprinkle on 2006-05-30
go in ur win xp os and format it to ntfs fat32 has big issues i repeat fat32 has big issues!!:mrgreen:

---

### Post by kokas on 2006-05-30
But the purpose of having the FAT32 was to be able to use it to read/write in XP and Ubuntu :( 
Is there any other way ?

---

### Post by Sutekh on 2006-05-30
[quote=kokas]Ok I kind of fixe the fstab file and now it doesn't give me any error messages. I'm also able to acess the FAT32 partition I created trough a VFat I created in the root folder with the name Backup...I followed the instructions in the same page for the FAT32 partitions...
One thing I don't understand is why the partition is created has a Virtual Fat that shows only in the root folder instead of a Disk in the desktop like the other partitions. Or at least if I could create a shortcut in the desktop would be ok.[/quote]Open the Configuration Editor from the Applications -> System Tools menu 

Then expand the apps -> nautilus -> desktop side bar.  

Make sure that the volumes_visible box is checked.

Does the partition appear?

If not, open Nautilus (the file browser) and use the middle mouse button to drag a shortcut of the partition to the desktop

---

### Post by kokas on 2006-05-30
Thanks a lot...I will try when I get home...

---

### Post by kokas on 2006-05-30
Hi there...the first method didn't worked because it was already set to visible....I think it may have something to do with the type of partition VFAT...I had to mount it manually trough the edit of the fstab file so I think that may be the cause
But the Shortcut method did work and I learned something new...I wasn't able to create shortcuts till now :D

---

