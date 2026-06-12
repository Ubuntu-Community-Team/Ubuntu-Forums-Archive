---
title: "new hard drive mounting; external"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by uzybear on 2007-09-12
ok, so i hooked up my external seagate ide USB drive and used gparted to format it; msdos disklabel, ext3 formatting

so, it shows up as mounted but i can't seem to change anything; the only folder in the "disk" is "lost+found" and i can't modify that or delete it; can't add files, can't make new folders

do i need to get admin privaledges or something?

---

### Post by annda on 2007-09-12
ext3 filesystem uses user privileges to determine user access to files. when the drive is mounted, can you check the ownership and permissions of the drive and contents? use nautilus and right-click to properties. what do you get in the permissions tab?

normally you would be able to set the ownership and permissions for the disk in the fstab file, but a USB disk will probably need a manual adjustment.

---

### Post by uzybear on 2007-09-12
yeah, it says "owner: root" and at the bottome "you are not the owner, so you can't change these partitions" which i find pretty funny, i don't remember stealing the drive :)

what do i do? i'm a full-on newb

---

### Post by annda on 2007-09-12
you probably formatted the drive using root privileges.  the easiest way i can think of to get your rights back is is to run the file manager as root (ALT+F2 > gksudo nautilus), navigate to the disk in filesystem > media and change the owner group to admin (of which you are certainly a member) and select all the possible permissions to the group.

if you want to read more, here goes info on permissions (terminal-wise):
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by uzybear on 2007-09-12
brilliant; all is well; you da man :)

---

### Post by uzybear on 2007-09-12
so i know, how exactly did i format with root privaledges? was it cuz i used "sudo fdisk -l" earlier in terminal? my ubuntu is completely new and i have hardly changed anything

---

### Post by uzybear on 2007-09-12
i have another problem; it says "cannot eject" when i try to eject, and if i unplug it it tells me it was not safe

---

### Post by uzybear on 2007-10-03
can anyone help me eject this drive?>

---

### Post by defrex on 2007-10-03
It usually says that if the system is still reading a file from the drive. Perhaps you have music on there that Rhythmbox is looking at or something? Try closing every app, and then ejecting.

---

