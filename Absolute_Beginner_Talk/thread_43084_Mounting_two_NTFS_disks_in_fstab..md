---
title: "Mounting two NTFS disks in fstab."
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-20
I just tried to mount my C: (hda1) and D: (hdb2) disks in fstab to have them mounted as default. They are both NTFS-disks and C: is used as my system-disk while D: is used for storage.

Here's what my new fstab look like:> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/home/kamine/Mounted/hda1	ntfs	unmask=0222	0	0
/dev/hdb2	/home/kamine/Mounted/hdb2	ntfs	unmask=0222	0	0


and here's the message I get when trying to reload fstab to get my disks:> 
kamine@ubuntu:~$ sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


How do I solv this? I am very certain that they are both NTFS-disks. C: was formated with the Windows XP Pro boot-CD while D: was formated in Partion Magic 8.x.

//Trojan1313

EDIT:
I used [http://ubuntuguide.org](http://ubuntuguide.org) for guidance.

---

### Post by Ride Jib on 2005-06-20
Well, the first thing I see right off the bat is, you need to use "umask" not "unmask." Otherwise, your fstab file looks good.

---

### Post by Trojan1313 on 2005-06-20
[QUOTE=Ride Jib]Well, the first thing I see right off the bat is, you need to use "umask" not "unmask." Otherwise, your fstab file looks good.[/QUOTE]
Oh, wops...
Hate that in Linux, had enormous troubles with umount as well 'cause no one noticed it. I write it 'cause it seems more logical to me, guess I'll have to get used to dropping the n. :)

Thanks a million times. :)

---

