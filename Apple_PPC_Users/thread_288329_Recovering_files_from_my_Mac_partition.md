---
title: "Recovering files from my Mac partition"
date: 2006-10-29
forum: Apple PPC Users
---

### Post by maxmartin on 2006-10-29
I have an iBook G4 which I dualboot with OSX and Ubuntu. I also just got a new MacBook (which I'm writing this with). Recently my iBook crashed, and subsequently it will not boot successfully in OSX, but it will boot in Ubuntu. I am trying to rescue some files from my Mac partition to my external hard drive. I have mounted both under the media/ directory, but I cannot seem to get it to write to my external hard drive. When in my media directory, this is the result of ls -l (hd is my external hard drive, mac is my other partition):


lrwxrwxrwx 1 root root    6 2006-06-13 01:28 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-06-13 01:28 cdrom0
drwxr-xr-x 1 root root   19 2006-10-15 20:35 hd
drwxrwxr-t 1 root   80   42 2006-10-26 17:30 mac

When I try dragging and dropping folders from my other partition to my external using the file browser, it says I don't have permissions to write to the folder. I've tried using chmod and cp, but my command-line skills have gotten embarrassingly rusty recently, so no luck...any advice? It'd be awesome if any of you could help me recover this stuff.

EDIT: Sorry, just remembered - I tried accessing the computer by putting it in Target mode, and while the computer displayed the FireWire logo as though it was working, my MacBook didn't recognize it.

---

### Post by stmiller on 2006-10-29
$ sudo -s

to get a root shell

then 

$ nautilus

Sometimes having an OS X drive/partition with journaling enabled is problematic.

---

### Post by maxmartin on 2006-10-29
With root it still says I don't have the permissions, and if I try and change them it says I can't because it's a read-only file system (for either one).

---

### Post by Torrance on 2006-10-29
What file system is the external hard drive using? If it is HFS+ Ubuntu will not be able to write to it. I'd suggest formatting it as plain HFS or even FAT32. You sound like you've done everything else right.

---

### Post by maxmartin on 2006-10-29
Oh. Well, unfortunately all of my music is stored on my external, and I don't have anywhere else to put it...I guess I can try burning some discs with the data I want.

---

### Post by Torrance on 2006-10-29
How about resizing and partitioning the external harddrive? GParted is a nice graphical tool to do this, and it can resize HFS+ systems fine. Simply make it smaller, create a new partition (say FAT32) and put the files you want to save there.

---

