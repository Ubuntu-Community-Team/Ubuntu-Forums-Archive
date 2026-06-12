---
title: "Samba and Rsync"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by Nomad_01 on 2005-11-01
I was wondering if it's possible to mirror an ntfs partition to a fat32 partition on another computer.

The setup:
NTFS partition on Wife's computer.
FAT32 Partition on mine.
Those computers are networked together through a switch.

On Brandie's computer (my wife) there's an external harddrive that has our family pics on it. I want to have any changes to that partition made to my FAT32 partition say, once a night. I understand that I am supposed to be able to use rsync for this along with cron. But my problem is that I don't know how to reference Brandie's partition in the rsync command since the only path name I've ever seen was something like smb://BRANDIE/MEDIA(F). But this doesn't seems to work with rsync.

If anyone can help shed some light on this subject I'd be greatly appreciative.

---

### Post by mlomker on 2005-11-10
I think you'd have to [use SMB to mount ]("http://www.ubuntuguide.org/#mountunmountnetworkfolders")the drive to a local directory and then use rsync against that local mount point.

---

