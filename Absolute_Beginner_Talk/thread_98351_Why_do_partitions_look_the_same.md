---
title: "Why do partitions look the same?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by Books on 2005-12-03
I am using Kubuntu and have two drives with an NTFS partition and three FAT32 partitions. I mounted them and just now I looked under "Storage Media" in Konqueror and it looks like the contents of each partition outside of the Linux root partition are *identical*! :confused: 

It says in "media:/" in Konqueror:
- Hard Disk (hda1)
- Hard Disk (hda5)
- Hard Disk (hda6)
- Hard Disk (hdb1)
- Hard Disk (hdb5)

The actual contents of the partitions are totally different. I use one partition as a backup and one as archives, and I do not want the contents of the drives mixed up. But it looks that way in Konqueror. All the partitions outside of hdb1 -- the Linux root -- are the showing the same files.

Not only that but after I installed Linux I went to one of the partitions using Windows and renamed some of the folders. The changes aren't showing up. (This is scaring me.)

How do you know what is physically on what drive? And how do you copy from one drive to another and *know* what drive that data is on?

I thought "mounting" was letting Linux see the contents of FAT32 drives. Did I do something wrong?

Thank you!

Books

---

### Post by jorn on 2005-12-03
Hi!
Have you mountet the drives correctly?
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
Jorn

---

### Post by Books on 2005-12-03
[QUOTE=jorn]Hi!
Have you mountet the drives correctly?
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
Jorn[/QUOTE]


I thought I did. I followed those directions exactly with the instructions under "How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?"

[B]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/B]

When I came to the part where it says...

*Append the following line at the end of file*
**/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0**

I saw that they were the same directions for all the FAT drives. I have 3 FAT partitions in addition to the NTFS partition. So I copied the text over at the same time, substituting the new drive letters.

Here is my /etc/fstab:
-----------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[B]/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb5       /media/windows  vfat    iocharset=utf8,umask=000   0       0[/B]
------------------

Did I mess something up by copying over the last 4 lines all at once instead of going through all that *sudo mkdir /media/windows -- sudo cp /etc/fstab  /etc/fstab_backup -- sudo gedit /etc/fstab*  stuff for each drive separately?

The contents of the FAT and NTFS partitions look exactly alike. Even the NTFS partition is only showing part of my data and none of the Windows files.

Books

---

### Post by Books on 2005-12-03
Me again.

Wait, I just had a thought -- does Linux have to mount standard FAT32 drives? The instructions say to mount *Windows* FAT drives... but Windows is only on my NTFS partition.

Does Linux read FAT drives without mounting and maybe mounting a non-Windows booting partition is what is causing the confusion?

I just checked by booting Windows and my files are all still where they should be on each drive. It's just that Linux is seeing the drives as having the same content for some reason.

Books

---

### Post by jorn on 2005-12-03
Hi again!
You must have the correct fat and ntfs directoris according to fstab but they must be differen for each drive.
example:
/dev/hda1 /media/windows1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/windows2 vfat iocharset=utf8,umask=000 0 0
/dev/hda6 /media/windows 3vfat iocharset=utf8,umask=000 0 0
/dev/hdb5 /media/windows4 vfat iocharset=utf8,umask=000 0 0

mkdir /media/windows1
mddir /media/windows2
and so on
you can name them whatever you want but always like in fstab
Does this help you?
Jorn

---

### Post by Books on 2005-12-03
[QUOTE=jorn]Hi again!
You must have the correct fat and ntfs directoris according to fstab but they must be differen for each drive.
example:
/dev/hda1 /media/windows1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/windows2 vfat iocharset=utf8,umask=000 0 0
/dev/hda6 /media/windows 3vfat iocharset=utf8,umask=000 0 0
/dev/hdb5 /media/windows4 vfat iocharset=utf8,umask=000 0 0

mkdir /media/windows1
mddir /media/windows2
and so on
you can name them whatever you want but always like in fstab
Does this help you?
Jorn[/QUOTE]

Jorn,

Thank you! Thank you! Thank you! Yes, I think that was the problem. I did what you said and used "mkdir /media/g_part" etc to create folders with the same designation as my Windows folders for familiarity, then updated my fstab...

------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[B]/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/g_part  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /media/d_part  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb5       /media/f_part  vfat    iocharset=utf8,umask=000   0       0[/B]
------------

Did I get it right?

I rebooted and sure enough, from first glance, it looks like my files are where they should be. I can even see the Windows C:/ directory contents which I couldn't before. No wonder nothing made sense! :rolleyes: 

Jorn, you are my favorite human being for the day! I award you with many :KS :KS  :KS :KS :KS

Thank you, Jorn!!!

Books

---

### Post by Books on 2005-12-03
Follow-up Question:

I just noticed in the contents of my /media/ directory that the DVD and the floppy are doubled...

media
*- cdrom*
- cdrom0
- d_part
*- floppy*
- floppy0
- f_part
- g_part
- windows

How did the cdrom and floppy get doubled? In the sidebar in Konqueror "*cdrom*" and "*floppy*" are italicised, the "cdrom0" and "floppy0" are not. I didn't mount them -- or did I? I don't think so. That part of the file came that way.

Books

---

### Post by jorn on 2005-12-03
Back again!
I am not sure of this.
The ones with the arrows are kind of links. Don't ask me for what purpose. I simply deleted them because they were irritating.
Jorn

---

### Post by Sanne on 2005-12-03
[QUOTE=jorn]The ones with the arrows are kind of links. Don't ask me for what purpose. I simply deleted them because they were irritating.[/QUOTE]

Please don't do this! Symlinks to drives are usually in there because programs might expect those mountpoints to exist. For example, there's a directory /cdrom which links to /media/cdrom which links to /media/cdrom0. I would really not mess with those!

---

