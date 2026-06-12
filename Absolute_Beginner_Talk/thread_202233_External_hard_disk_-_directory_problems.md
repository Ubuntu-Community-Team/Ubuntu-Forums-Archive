---
title: "External hard disk - directory problems"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-06-23
Hi

I've recently bought an external hard drive - a WD 80G My book. I want to use it for archieving key folders, such as /home/.

It appears happily on my desktop, and I've used the gui to create a folder in the drive called Backups. I can also use the gui to drag and save files into this folder. However, when I change to the root directory and run 'ls' Backups appears in black, instead of the regular blue of a directory. Also, when I try to copy to Backups from the command line, or try to change to the Backup directory, I get the message

Backups: Not a directory.

It may not be relevant, but when I go System>Administration>Disks, and look under partitions, the Access Path book says 'none'.

No doubt it's trival, but what am I doing wrong?

All help much appreciated.

Best regards

Roger D

---

### Post by Apple 101 on 2006-06-23
Make sure you specify the absolute path to the drive, for example: /media/your-drive-name/Backups.

Remember, Linux is case sensitive.

---

### Post by RogerD on 2006-06-23
Hi
You said:
Make sure you specify the absolute path to the drive, for example: /media/your-drive-name/Backups.

Remember, Linux is case sensitive.

This is what I'm getting:

roger@roger-desktop:~$ cd /
roger@roger-desktop:/$ ls
Backups  cdrom  home        initrd.img.old  mnt   root  sys  var
bin      dev    initrd      lib             opt   sbin  tmp  vmlinuz
boot     etc    initrd.img  media           proc  srv   usr  vmlinuz.old
roger@roger-desktop:/$ cd /media/My Book/Backups
bash: cd: /media/My: No such file or directory
roger@roger-desktop:/$

When I click on properties for the hard disk icon on my desktop, My Book is the name I'm given.

Something still not right.

---

### Post by Apple 101 on 2006-06-23
Okay, I didn't realise it had been mounted like that.

Try: cd /Backups

To allow for spaces in file names:

part1/ part2

For example:  My/ Book

Please post the output of: cat /etc/fstab

---

### Post by x64Jimbo on 2006-06-23
Try going into your /media directory and then listing the contents. You should be able to see the directory in there, and what it might be called differently.

---

### Post by RogerD on 2006-06-23
Hi 
When I run ls in / I get My Book as a nice blue directory. However, attempts to change directory to My Book just yields the message:'My: No such file or directory'.

cat /etc/fstab yields:

roger@roger-desktop:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm not sure what I'm looking at here, but I don't seem to see my external drive.

---

### Post by Apple 101 on 2006-06-23
[QUOTE=RogerD]Hi 
When I run ls in / I get My Book as a nice blue directory. However, attempts to change directory to My Book just yields the message:'My: No such file or directory'.[/QUOTE]

Open a command prompt (terminal window):
*cd /My\ Book* or *cd /media/My\ Book*

---

