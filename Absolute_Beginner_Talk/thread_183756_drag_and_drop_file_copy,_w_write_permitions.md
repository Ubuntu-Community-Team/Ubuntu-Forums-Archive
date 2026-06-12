---
title: "drag and drop file copy, w/ write permitions"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by ws6fire on 2006-05-28
I'm very new to linux.  The only comand line I know is back in DOS days... ;)

I have ubuntu installed on a machine, I have an ntfs drive (from another computer) connected via usb, I can see the files fine.  I copy it over to another drive that's fat32.  Copies fine, but locks everything! I can't del files unless I open each and every file properties and clock "Write" under Permissions\owner: 

Is there a way to change all of them at one time? or copy over without having them get locked like that?

Thanks for your help!

***background on what I'm doing*** I have a ntfs drive from a windows machine that has gone so bad whenever I connect it to a windows machine it reboots right away. I'm just saving data files off the drive.***  Ubuntu has cought my eye... I'll be looking into it more and more. :D

---

### Post by ifokkema on 2006-05-28
[QUOTE=ws6fire]I have ubuntu installed on a machine, I have an ntfs drive (from another computer) connected via usb, I can see the files fine.  I copy it over to another drive that's fat32.  Copies fine, but locks everything! I can't del files unless I open each and every file properties and clock "Write" under Permissions\owner:

Is there a way to change all of them at one time? or copy over without having them get locked like that?[/QUOTE]

Hi,

NTFS is mounted read only, so files you copy from there are read only as well. But I'm afraid you're going to need your console... :)

cd into the directory where your copied files reside on the FAT32 drive (just like the old DOS days...) and run:
```
chmod -R u+w *
```

This will provide the file owner (you) write privileges.

Hope this helps,

Ivo

---

### Post by mlind on 2006-05-28
I get the same when I copy file over from NTFS share. File always get's 555 permissions. I usually just chmod do 644 for file or directory contents.

from terminal, do

chmod 644 *file* or chmod -R 644 *directory*

---

### Post by ws6fire on 2006-05-28
will that drop down the full directory tree?

Sounds easy enough. :D

(knees shaking...)

---

### Post by ifokkema on 2006-05-28
[QUOTE=ws6fire]will that drop down the full directory tree?

Sounds easy enough. :D

(knees shaking...)[/QUOTE]

Hi,

The -R option tells chmod to recurse in all directories given.

Please NOTE that chmod 644 will directly set all permissions rw-r--r--, which will be a problem with directories. If you use the u+w flag, it will give the user write privileges, but leave all other permissions set like they are (at least rx for directories).

Ivo

---

### Post by RRS on 2006-05-28
Try editing your fstab;
```
sudo gedit /etc/fstab
```

```
/dev/hda1       /media/windows ntfs nls=utf8,umask=000,uid=1000,gid=1000 0    0
/dev/hda6       /media/common vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 0

```

Substitute your terms for "hda1", "hda6", "windows", and "common".

This will mount both drives automatically at boot-up with you (user) as owner and then under properties you'll be able to select read for the ntfs drive and read/write for the fat32.

---

### Post by mlind on 2006-05-28
[QUOTE=ifokkema]Hi,

The -R option tells chmod to recurse in all directories given.

Please NOTE that chmod 644 will directly set all permissions rw-r--r--, which will be a problem with directories. If you use the u+w flag, it will give the user write privileges, but leave all other permissions set like they are (at least rx for directories).

Ivo[/QUOTE]

yup, you're right. 644 isn't suitable for directories.
sorry about that.

---

