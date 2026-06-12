---
title: "Recovering Partititon Using Ubuntu Live CD"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by GTonizuka on 2006-09-11
hello everyone,
i dont know what has happened just now, i am not sure if my message has been sent, so i write again...
i was using 60GB HDD as one partititon, i decided to install Ubuntu so i wanted to divide this partition into two (55GB and 5GB) using Partititon Magic. But this great(!) tool gave me an error in the middle of resizing the partition and now everything is blank. 
i cannot mount my windows NTFS system on Ubuntu live, here is the error message:

 sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=02

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

System>administration>disks sees the drive as 55GB (55,89 actually) as dev/hda, however, partitions tab shows the partiton as dev/hda1, filesystem unknown. 

is there any way to recover my lost data using Ubuntu Live CD?
any help would be appreciated!
thanks.

---

### Post by bulldog on 2006-09-11
I rather would use the Windows cd-rom to try to recover your data.

If you want to install Ubuntu on a 5GB partition,I warn you,that's not much space.
I should make minimal a 10GB partition instead.

---

### Post by GTonizuka on 2006-09-11
thanks bulldog
using windows cd solved the problem, i am again under WXP right now. 
for the ones having the same or similar problem:

boot with windows cd
go to recovery console
perform disk checking by typing CHKDSK

now, the actual question is, is there a better way to partition my drive, so that i can reserve a 10GB to install Ubuntu?

---

