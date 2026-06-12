---
title: "Viewing my Windows XP files"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Groth on 2006-02-01
I just installed ubunutu linux as a second OS in it's own partition, and I was wondering if it's possible somehow to view the XP part of my harddrive from within linux. I'm using an NTFS file system. Thanks for your help.

---

### Post by Cesium on 2006-02-01
[QUOTE=Groth]I just installed ubunutu linux as a second OS in it's own partition, and I was wondering if it's possible somehow to view the XP part of my harddrive from within linux. I'm using an NTFS file system. Thanks for your help.[/QUOTE]
 
Yes.  Below is how.  And here is the link to how to do this in the Unofficial Ubuntu guide: [ http://www.ubuntuguide.org/#mountunmountntfs]("http://www.ubuntuguide.org/#mountunmountntfs")

[COLOR="Blue"]Q: How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?
   1. Read General Notes
   2. Read How to list partition tables?
   3.
      e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
           Local mount folder: /media/windows
   4. To mount Windows partition
      sudo mkdir /media/windows
      sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
   5. To unmount Windows partition
      sudo umount /media/windows/[/COLOR]

AND:
[COLOR="Red"]Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?
   1. Read General Notes
   2. Read How to list partition tables?
   3.
   e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
           Local mount folder: /media/windows
   4.
      sudo mkdir /media/windows
      sudo cp /etc/fstab /etc/fstab_backup
      sudo gedit /etc/fstab
   5. Append the following line at the end of file
      /dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
   6. Save the edited file (sample)
   7. Read How to remount /etc/fstab without rebooting?[/COLOR]

You can't write to NTFS, but you can read the files.  I hope that helps :-D

---

### Post by Groth on 2006-02-01
Works wonderfully, thanks a lot!

---

### Post by teddy69 on 2006-02-01
something I found useful was to install xp on a FAT32 partition, it had to be under 30 gigs though which was good enough for me, that way linux can read and write to it

---

### Post by beaulanger on 2007-01-13
Thanks very much. I really appreciate it. I think  Mepis would do it by default:.
Beau

---

