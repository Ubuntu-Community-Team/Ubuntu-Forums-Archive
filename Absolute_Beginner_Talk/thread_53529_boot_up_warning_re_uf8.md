---
title: "boot up warning re uf8?"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by Darkscot on 2005-08-01
I have Ubuntu & XP on a dual boot system.  I have just converted the partition with all my data from NTFS to FAT32 (with Partition Magic) so I can read & write with both Linux and XP.  Because of this I had to edit my fstab file which i did using the instructions in the Ubuntuguide.  I changed the relevant line from:
[B]
/media/windows  ntfs    nls=utf8,umask=0222 0       0[/B]

to 

**/media/windows  vfat    iocharset=utf8,umask=000   0       0**

This works ok, the drive is mounted and I can read/write but I get an error message on boot up.  This says some thing like  "utf8 character set is not recommended for FAT32 as  file names will be case sensitive"  

Is this likely to be a problem and if so what is the solution?

---

### Post by phen on 2005-08-01
Windows' filesystem is not case sensitive. therefore, Hello.txt and hello.txt in the same directory are the same files. If you mount a FAT partition as utf8, linux accesses it case sensitive. therefore linux would let you save Hello.txt and hello.txt (i think it would overwrite without warning...).

thats the theory. i use fat partitions mounted with utf8 and never had problems. maybe others can help? 

cheers,

kai

---

### Post by Darkscot on 2005-08-02
Well so far I have not experienced any problems.  I try to stick to lower case file names anyway.

---

### Post by Jingo on 2005-08-04
I have some problems with my external USB harddrive.

It seems there might be problems using locale characters like æøå in filenames when FAT mounted utf8!!!

How can I change this? My USB hdd is automounted... no entry in fstab!

---

