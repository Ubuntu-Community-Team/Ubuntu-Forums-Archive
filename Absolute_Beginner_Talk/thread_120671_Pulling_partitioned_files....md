---
title: "Pulling partitioned files..."
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by abrainlessdude on 2006-01-23
I need to pull over some files across my partition (about 100 itunes songs).  I have windows (Professional XP) and ubuntu.  Is it possible to pull those files across the partition?

---

### Post by dueY on 2006-01-23
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

If by 'pull' you just mean you need to access them, then mounting your NTFS drive is the answer.

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=dueY][http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)[/QUOTE]
Thank you, but that didnt work, because i dont have an "hda1"

---

### Post by dueY on 2006-01-23
[QUOTE=abrainlessdude]Thank you, but that didnt work, because i dont have an "hda1"[/QUOTE]

"e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)"

Go System > Administration > Disks 
Click on your harddrive under Storage List
Click the partitions tab on the right
Look for the NTFS one

---

### Post by mcduck on 2006-01-23
run 'sudo fdisk -l' to get a list of your partitions.

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=mcduck]run 'sudo fdisk -l' to get a list of your partitions.[/QUOTE]
I got this...
[quote=Terminal]```
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        2221    17775922+   7  HPFS/NTFS
/dev/sda3            2222        3585    10956330   83  Linux
/dev/sda4            3586        3648      506047+   5  Extended
/dev/sda5            3586        3648      506016   82  Linux swap / Solaris

```[/quote]


So what should I be doing.... ?

---

### Post by dueY on 2006-01-23
/dev/sda2  instead of /dev/hda1

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=dueY]/dev/sda2  instead of /dev/hda1[/QUOTE]
ok. I did that, now how do I play the music files??? lol, thank you so much everyone for your help so far.

---

### Post by dueY on 2006-01-23
[QUOTE=abrainlessdude]ok. I did that, now how do I play the music files??? lol, thank you so much everyone for your help so far.[/QUOTE]

Open up your music player.  Load the files. :D 

They should be located in /media/windows/whatever

for example: /media/windows/documents and settings/brainless/my music  or wherever you keep your music on your Windows partition

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=dueY]Open up your music player.  Load the files. :D 

They should be located in /media/windows/whatever

for example: /media/windows/documents and settings/brainless/my music  or wherever you keep your music on your Windows partition[/QUOTE]
okay, this is going to sound really bad... but there's nothing in that file :(

---

### Post by dueY on 2006-01-23
[QUOTE=abrainlessdude]okay, this is going to sound really bad... but there's nothing in that file :([/QUOTE]

The /media/windows?
Or the fake file path that I made up as an example? :p

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=dueY]The /media/windows?
Or the fake file path that I made up as an example? :p[/QUOTE]
in /media/windows

---

### Post by dueY on 2006-01-23
Ok type this in terminal:
sudo gedit /etc/fstab

Make sure it says this in the fstab:
```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=dueY]Ok type this in terminal:
sudo gedit /etc/fstab

Make sure it says this in the fstab:
```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```[/QUOTE]
it does. does it matter that it my music isint in "media" folder on the windows drive?

---

### Post by dueY on 2006-01-23
[QUOTE=abrainlessdude]it does. does it matter that it my music isint in "media" folder on the windows drive?[/QUOTE]

No.  The media file in this case isn't on your Windows partition.  It's just the conventional folder for stuff you mount.

Are you sure you did the
```
sudo mkdir /media/windows
``` step?

Also this may be a stupid question, but did you save the fstab file after editing it?

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=dueY]No.  The media file in this case isn't on your Windows partition.  It's just the conventional folder for stuff you mount.

Are you sure you did the
```
sudo mkdir /media/windows
``` step?

Also this may be a stupid question, but did you save the fstab file after editing it?[/QUOTE]Yes I did save. Maybe it's not on sda2 though?  I'm sorry for causing so much trouble.... thanks for the help again.

---

### Post by dueY on 2006-01-23
[QUOTE=dueY]
Go System > Administration > Disks 
Click on your harddrive under Storage List
Click the partitions tab on the right
Look for the NTFS one[/QUOTE]

Try this and make sure it is /dev/sda2  (it should be, given the output of sudo fdisk -l you pasted earlier...)

---

### Post by abrainlessdude on 2006-01-23
lol, i think that SDA1 is the windows boot....

---

### Post by carlosqueso on 2006-01-23
You need to either restart your computer or type ```
sudo mount -a
``` to get it to mount the drives in fstab.....did you do that?  

EDIT: also you need sda**2** not sda1

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=carlosqueso]You need to either restart your computer or type ```
sudo mount -a
``` to get it to mount the drives in fstab.....did you do that?[/QUOTE]
no..... I did that, but when I did, it did this

```
marc@ubuntuLp:~$ sudo mount -a
mount: special device /dev/hda2 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by dueY on 2006-01-23
[QUOTE=abrainlessdude]no.....[/QUOTE]

D'oh I thought it was kind of obvious from the link I posted from the first reply to reboot, but I guess not ](*,)

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=dueY]D'oh I thought it was kind of obvious from the link I posted from the first reply to reboot, but I guess not ](*,)[/QUOTE]
when i did that i got this.


```
marc@ubuntuLp:~$ sudo mount -a
mount: special device /dev/hda2 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

thanks for all your help guys.....

---

### Post by carlosqueso on 2006-01-23
okay...you need to take out the hda1 line in your fstab, because you only have SCSI drives, and change the sda1 to sda2.  Then try the ```
sudo mount -a
``` command again.  HOPEFULLY (with technology, there's no gaurentee), that should work.

---

### Post by abrainlessdude on 2006-01-23
[QUOTE=carlosqueso]okay...you need to take out the hda1 line in your fstab, because you only have SCSI drives, and change the sda1 to sda2.  Then try the ```
sudo mount -a
``` command again.  HOPEFULLY (with technology, there's no gaurentee), that should work.[/QUOTE]
This is what I have in there

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

I'm guessing I should take out the hda2 line, but before I do anything, I want to run it by you guys.   ([-o< it works, 'eh :P)

---

### Post by dueY on 2006-01-23
Yes take out the hda2 and you only need the sda1 there once.

---

### Post by carlosqueso on 2006-01-23
Actually....take out the bottom three lines and replace them with ```
/dev/sda2 /media/windows ntfs nls=utf8,umask=0222 0 0
``` and it should work

---

### Post by abrainlessdude on 2006-01-23
yay, it works, thank you everyone.  I owe you all a big favor, if I can ever help ya'll with something, just ask :)

---

### Post by carlosqueso on 2006-01-23
You're welcome....glad to help :D

---

