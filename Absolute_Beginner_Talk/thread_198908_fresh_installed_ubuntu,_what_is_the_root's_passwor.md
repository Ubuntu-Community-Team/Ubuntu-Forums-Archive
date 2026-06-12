---
title: "fresh installed ubuntu, what is the root's password?"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by babyboss on 2006-06-17
I just installed the new version of the ubuntu, with formatting everything. What is the root password supposed to be?

---

### Post by mlind on 2006-06-17
For default, root account is "disabled" on Ubuntu.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by babyboss on 2006-06-17
I partition my harddrive into two partitions, one for windows, one for ubuntu. I am able to access to the window partition under ubuntu. However, I want to edit an microsoft excel file under ubuntu. Is there a way to open the excel file with write mode on? Thanks

---

### Post by Kilz on 2006-06-17
[QUOTE=babyboss]I partition my harddrive into two partitions, one for windows, one for ubuntu. I am able to access to the window partition under ubuntu. However, I want to edit an microsoft excel file under ubuntu. Is there a way to open the excel file with write mode on? Thanks[/QUOTE]
If the document is on a windows partition, and its windows 2000 or Windows XP they use ntfs and it is not possible to write to it from Linux. But you could make a small fat32 partition and store documents there you need to write to with both OS's. 
Some say its possible, but you take a chance of destroying the partition and/or the document. It isnt worth the risk imho. You could save it to Linux and edit it, but you wouldnt be able to access it on the linux partition from windows.

---

### Post by Shay Stephens on 2006-06-17
[QUOTE=babyboss]I partition my harddrive into two partitions, one for windows, one for ubuntu. I am able to access to the window partition under ubuntu. However, I want to edit an microsoft excel file under ubuntu. Is there a way to open the excel file with write mode on? Thanks[/QUOTE]

You can open a nautilus window in "root mode" by typing in
```
sudo nautilus
```

And that will let you do whatever you want.

Info on mounting partitions here:
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by mlind on 2006-06-17
[QUOTE=babyboss]I partition my harddrive into two partitions, one for windows, one for ubuntu. I am able to access to the window partition under ubuntu. However, I want to edit an microsoft excel file under ubuntu. Is there a way to open the excel file with write mode on? Thanks[/QUOTE]

If you mean that you can write to NTFS drive, then yes it's possible but discouraged.
NTFS write support is kinda "experimental", but search threads about fuse and ntfs
if you want it.

If you just want to edit file from foreign partition and save it on your home folder,
then you must mount your with read permissions described on [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by mlind on 2006-06-17
I suggest though that you don't use nautilus with root privileges unless you know
exactly what you're doing.

---

### Post by babyboss on 2006-06-17
haha.. What I want to do is edit a file from a foreign partition and save it on the foreign partition. perhaps, I am not allowed to do that due to the fact that it's a nfts file system?

---

### Post by aysiu on 2006-06-17
[QUOTE=mlind]I suggest though that you don't use nautilus with root privileges unless you know
exactly what you're doing.[/QUOTE]
Well, it's no different from using the *sudo* command from the terminal.

And, honestly, it doesn't solve the problem at hand, which is that the NTFS partition is probably not mounted with the proper permissions, and even if it were, the permissions would be read-only.

---

### Post by aysiu on 2006-06-17
[QUOTE=babyboss]haha.. What I want to do is edit a file from a foreign partition and save it on the foreign partition. perhaps, I am not allowed to do that due to the fact that it's a nfts file system?[/QUOTE]
Exactly.

The default behavior mounts NTFS (for some strange reason) as not readable.

If mounted properly, NTFS is read-only.

FAT32 is read/write from both Windows and Ubuntu.

Ext3 (Ubuntu's native format) can be read/write from Windows with the help of [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by babyboss on 2006-06-17
NTFS partition is mounted, but only with read-only permission

---

### Post by babyboss on 2006-06-17
Thank you all very much. really appreciate for the quick responses.

---

### Post by mlind on 2006-06-17
[QUOTE=aysiu]Well, it's no different from using the *sudo* command from the terminal.[/QUOTE]

That's not what I meant. Using either one without knowing why is a no-no.

---

### Post by aysiu on 2006-06-17
[QUOTE=mlind]That's not what I meant. Using either one without knowing why is a no-no.[/QUOTE]
Good point. Now I get it.

---

