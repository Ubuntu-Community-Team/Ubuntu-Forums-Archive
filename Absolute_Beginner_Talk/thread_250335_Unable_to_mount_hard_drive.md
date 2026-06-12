---
title: "Unable to mount hard drive"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Ueler on 2006-09-03
I have to hard drives and I have install ubuntu on /dev/hda and also i have 
another drive /dev/hdd that has been left over from a windows xp box with some files on it I cann't access this drive /dev/hdd. Is there a way to mount it and save the files on it so I can access it? Thanks!

---

### Post by szf on 2006-09-03
If the install didn't catch that drive on install (or it was unplugged at the time) - I believe you should be able to mount it with:
[FONT="Fixedsys"]
$ sudo mount -t <format> /dev/hdx<n> /mnt/<temp mount point>
[/FONT]
That breaks down:
<format> - vfat (for FAT filesystems)... I assume there's some read-level support for NTFS with the ntfs option - be careful with that format however, help us, ubuntu forums? ... 

hdx<n> - where x is the hard disk drive letter and n is the partition number

<temp mount point> - you may want to create a subdirectory under /mnt (such as win)... assuming Ubuntu hasn't already created a /media/hdx link for it...

---

### Post by confused57 on 2006-09-04
Here's a link to mount Windows:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---

