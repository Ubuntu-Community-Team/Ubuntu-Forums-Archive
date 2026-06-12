---
title: "Installed Ubuntu this morning..."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by staib on 2006-10-14
Hi all,

Just love the look and feel of Ubuntu - and still in initial explorer mode...

Have set up a dual boot option (from the live - CD) and all seems fine but I am now trying to see the contents of my partition formerly known as the "C drive".

I get the following message...

"You do not have the permissions necessary to view the contents of "disks-conf-hda1".

Is this a Windows thing or is it relatively simple - I just wanted to access ssome music files...

Cheers,

Nick

---

### Post by petri on 2006-10-14
That was something new :)

Maybe you have to mount it if you haven't done it already.

---

### Post by Sef on 2006-10-14
> Is this a Windows thing or is it relatively simple - I just wanted to access ssome music files...


Yes, it is a Windows thing.  Most likely you're Windows file is NTFS, and that is proprietary.  Best way to share files is set up a partition which is formatted in either FAT32 or ext3 file system.  Both Windows and Linux can read and write to those file systems.

---

### Post by staib on 2006-10-14
Thanks guys.  Can I then use WinXP to copy existing files from the NTFS partition to the new ext3 partition?  

Is there no Ubuntu friendly app that can reach in and grab copies?  Im not trying to write back to the NTFS partition, but did assume I could read from there...

---

### Post by Sef on 2006-10-14
> Im not trying to write back to the NTFS partition, but did assume I could read from there...

That's correct. You should be able to read from there.

---

### Post by raul_ on 2006-10-14
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

U won't be able to write on your windows drive. I just use that to access my files because i'm too lazy for backups

---

### Post by jorn on 2006-10-14
If you dont't already know about this site:
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)
It was very helpful for me, especially in the beginning of my Ubuntu-adventure.
Further down there is describtion on how you mount mswindows partitions.

---

### Post by staib on 2006-10-14
Thanks again...

I am still trying to "read" my ntfs WinXP partition...

From the EasyLinux Wiki:
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Done that but I then get an error message (see under)

dad@dad-desktop:~$ sudo mkdir /media/windows
dad@dad-desktop:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,unmask=0222

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Am I doing anything obviously wrong?!  Cheers...

---

### Post by staib on 2006-10-14
This is what I get when I run nano - I expected to see "/dev/hda1" there somewhere...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by slibuntu on 2006-10-14
Actually to see an ext3 partition in XP, dont you need fs-driver? [http://www.fs-driver.com]("http://www.fs-driver.com")

---

### Post by jorn on 2006-10-14
To see the correct partition of your ntfs files do:
> sudo fdisk -l
To mount it on your already created /media/windows:
> sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
Note:It is "umask" not "unmask".I hope that makes the difference.

---

### Post by staib on 2006-10-14
Thanks Jorn!  Typing "umask", instead of "unmask", did the trick!  Must have been thinking of Zorro or summat :) 

Cheers Slibunto - that link will prove useful to see into Ubuntu from XP (not that I plan to be in XP too often, now)

Nick

PS - Off to figure out how to play those mp3 files now - I may be back...
PPS - I have already installed Automatix ;)

---

### Post by staib on 2006-10-14
...and am now playing my mp3 files - life is good! :)

---

