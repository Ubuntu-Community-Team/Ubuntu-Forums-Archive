---
title: "External HDD &quot;locked&quot;"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-01-20
I'm having trouble accessing my external hard drive. I just formated to an ext3 file system with gparted, but I am unable to write. The partition seems to have been mounted by root so it is not accessible.

[IMG]http://img.photobucket.com/albums/v608/Hellcom/HDDlocked.png[/IMG]

---

### Post by bodhi.zazen on 2007-01-20
```
sudo chown root:users <mount_point>
sudo chmod 770 <mount_point>
```

Where <mount_point> is you mount point (/media/sda1 or what have you)

---

### Post by Hellcom on 2007-01-20
Ok, now I can't even read the volume now, instead I get an error message:

> You do not have the permissions necessary to view the contents of "Nex"

---

### Post by bodhi.zazen on 2007-01-20
> **Hellcom said:**
> Ok, now I can't even read the volume now, instead I get an error message:

Can you post the output of:
```
ls -l /media
```Or wherever your mount point is ?

As well as your entry for fstab ...

Or, if for some reason you are not in the users group:

sudo chmod 777 <mount_point>

---

### Post by Hellcom on 2007-01-20
ls -l /media
total 20
lrwxrwxrwx  1 root root     6 2007-01-19 17:16 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-01-19 17:16 cdrom0
drwxr-xr-x  2 root root  4096 2007-01-19 17:16 cdrom1
lrwxrwxrwx  1 root root     7 2007-01-19 17:16 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-01-19 17:16 floppy0
drwxrwx--- 35 root users 4096 2007-01-20 22:30 Nex
drwxr-xr-x  2 root root  4096 2007-01-19 20:20 windows


and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5bb49ce4-ba5c-4a1d-94ac-bf23262804a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0670c461-8afd-49ee-abab-1af1e202f351 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Edit: Also, sudo chmod 777 <mount_point> allowed me to read again

---

### Post by bodhi.zazen on 2007-01-20
I am not sure, permissions look OK ...

with permissions of 777

Perhaps unmount and remount the drive ....

Test from a terminal (could you post the oputput):

```
touch /media/Nex/test
ls -l /media/Nex | grep test
```

Assuming your HD is mounted at /media/Nex (as it appears to me).

---

### Post by Hellcom on 2007-01-20
Remounted drive, still lack to permissions to write.

First command opened the file browser, nothing special there.

Second:
ls -l /media/Nex | grep test
-rw-r--r--  1 hellcom hellcom    0 2007-01-20 23:59 test****

---

### Post by bodhi.zazen on 2007-01-20
viola ;)

the first command> touch /media/Nex/test

Wrote an empty file "test" to the drive ....

As seen by the output:> s -l /media/Nex | grep test
-rw-r--r-- 1 hellcom hellcom 0 2007-01-20 23:59 test

[img]http://ubuntuforums.org/images/smilies/eusa_clap.gif[/img]

[list][*]Sorry for the delay in getting back :p
[*]you can delete the file test if you like
[*]You can write to it:```
cat /media/Nex/test
echo MEOW >> /media/Nex/test
cat /media/Nex/test
```

The first cat will return nothing (empty file), the second cat will meow ;)[/list]

---

### Post by Hellcom on 2007-01-21
Sorry was asleep.

Well the cat did meow :P

So now that one single text file is writable, but everything else is still locked. I can now create, copy, and delete files (write) on the top directory and on any new directory paths I create. However, all the files that were already there before this I still lack the permissions to do anything with other than read. There are also two weird new directories I have never seen before called "lost+found" that I lack the permission to read, and "Recycled", which like the others I lack the permissions to write. They are all under root btw.

[IMG]http://img.photobucket.com/albums/v608/Hellcom/Screenshot-1.png[/IMG]

Should I mention that I copied these files onto this hard drive using windows XP (with the FS windows drivers) while ubuntu wasn't writing? Does that matter?

Edit: Also, I'm still locked from editing the partitions table when in gparted (on ubuntu not on  gparted-livecd).

Edit Again: I just created a new directory in windows and put some files into it, and none of the new files are read-only (read/write now) under ubuntu. It seems it's only the partition tables and the files I transfered over during the re-formating period of the drive that are locked.

---

### Post by bodhi.zazen on 2007-01-21
Well, it seems you have a permissions problem.

It seems, as you say, the files are owned by root.

Is the file system, on the HD, ext3, FAT, or NTFS ? I am under the understanding it is ext3.

OK for shared files, chown to yourself rather then root.

Or chmod 777 

You should leave lost + found alone. It is a system fiel used in disk maintenance.

You can:

```
gksudo nautilus
``` to run anutilus as root.

sudo chown user:group <directory_or_file>
sudo chmod <directory_or_file>

sudo chmod 777 /media/Nex/TV/*

It may be easiest to do this in Windows where you have rw access to the files.

Let me know if you have trouble or further difficulties :)

EDIT:

Oh, and it is best to run gparted as root from a live CD. A partition need to be unmounted before you can edit it.

I am guessing you copied your files as root, thus they are owned as root ?

---

### Post by Hellcom on 2007-01-21
Ok, it's working now. Thanks a lot.

---

