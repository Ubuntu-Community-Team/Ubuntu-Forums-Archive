---
title: "second hard drive"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by pm32610 on 2007-08-08
How do I get Ubuntu to recognize my second hard drive? Or, is it there, I just don't know where to look? Any help would be appreciated. I have only started using Ubuntu within the last two days, original hard drive crashed so I lost windows and don't want to pay to reinstall, so I am starting from scratch. All my documents and such are on my secondary drive. Thanks

---

### Post by oilchangeguy on 2007-08-08
> **pm32610 said:**
> How do I get Ubuntu to recognize my second hard drive? Or, is it there, I just don't know where to look? Any help would be appreciated. I have only started using Ubuntu within the last two days, original hard drive crashed so I lost windows and don't want to pay to reinstall, so I am starting from scratch. All my documents and such are on my secondary drive. Thanks

welcome to ubuntu. but i've got to ask. what do you mean by, don't want to pay to reinstall windows? where did you get this idea?

---

### Post by Cypher on 2007-08-08
Open up a terminal and type
```

sudo fdisk -l

```
This should list all of your HD's and the partitions. You should hopefully see 2 HD's and one of them should list the NTFS/FAT32 partitions where your Windows XP installation used to be. You can now mount that partition in Ubuntu and recover your documents..

---

### Post by pm32610 on 2007-08-08
> **oilchangeguy said:**
> welcome to ubuntu. but i've got to ask. what do you mean by, don't want to pay to reinstall windows? where did you get this idea?

Windows came preloaded, I don't have my own liscense. So I will have to pay someone else to reinstall it, or buy my own liscense at $300.00

[QUOTE=Cypher]  Open up a terminal and type
Code:

sudo fdisk -l

This should list all of your HD's and the partitions. You should hopefully see 2 HD's and one of them should list the NTFS/FAT32 partitions where your Windows XP installation used to be. You can now mount that partition in Ubuntu and recover your documents..[/QUOTE]

When I do this, it asks for a password, but will not let me type anything else, what am I doing wrong?

---

### Post by oilchangeguy on 2007-08-08
if you bought the computer new, you should have a restore cd. or there is a restore partition on the hard drive. also if the computer has the windows coa sticker, you will have no reinstall problems, that involve money.

---

### Post by ron999 on 2007-08-08
> **pm32610 said:**
> 
When I do this, it asks for a password, but will not let me type anything else, what am I doing wrong?

The 'sudo' means that you are the supervisor. So type your password and hit enter.

---

### Post by jgrabham on 2007-08-08
And dont warroy that you cant see anything as you type - its so nobody can read your password over your shoulder.  Just type it and press enter

---

### Post by pm32610 on 2007-08-08
Ok, found that, but I guess my question should have been, I am still running two hard drives, (I replaced the one that crashed, it fried) so how do I get the second to show up under "file system", or "file browser" or whatever?

---

### Post by Inxsible on 2007-08-08
post the output of the following commands here. Maybe we can then help you figure out.

```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by pm32610 on 2007-08-08
Here is what I got from the fstab command. 

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         127     1020096    7  HPFS/NTFS
robby@pc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0       0

---

### Post by Inxsible on 2007-08-08
Open fstab with this command
```
gksudo gedit /etc/fstab
``` Add this line to the end of the fstab file ```
/dev/hdb1 /media/MyWinDrive ntfs-3g rw,auto,exec,user,locale=en_US.UTF-8 0 1
```Save and close the file.

Then create a folder under /media called MyWinDrive. you can actually choose any name, just make sure its the same at both places

```
sudo mkdir /media/MyWinDrive
```finally do a ```
sudo mount -a
```

EDIT : I am assuming you have already installed ntfs-3g which is required to get write access on ntfs drives.if not, then you will still be able to read the drive, but you will not be able to write to it.

HTH

---

