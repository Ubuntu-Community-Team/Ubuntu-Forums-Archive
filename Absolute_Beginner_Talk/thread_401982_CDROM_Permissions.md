---
title: "CDROM Permissions"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by rovernaut on 2007-04-05
I have installed codeweaver  Crossover and after the installation I find I can no longer access any files on any CD I place in the CDROM.
 I checked properties and it says 
Ownership  is 
User : root
Group: root.
How do I change the Group to allow access to the files.

---

### Post by dannyboy79 on 2007-04-05
try this for your fstab entry. unmount the cdrom, then remount it. also, i have access to files and my folder (/cdrom) has it's owner being root:root. just make sure that the permission's match mine. they are as follows:

this is the cdrom symlink under /
lrwxrwxrwx   1 root root    11 2006-09-11 08:15 cdrom -> media/cdrom

these are the 2 cdrom's under /media/
lrwxrwxrwx  1 root root    6 2006-09-11 08:15 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-09-11 08:15 cdrom0


also, the folder within / called cdrom is merely a symlink to /media/cdrom, then that is merely a symlink to /media/cdrom0 so make sure you set each of the permissions correctly. it may be because it's not executable, for a folder to be able to be read and files moved from it, I believe it has to executable. notice how all mine have the x.

to change this, you would simply run

sudo chmod +x /path

(NOTE: path just means the path of the folder you want to add executable permissions for.)
let me know how it goes. good luck

---

