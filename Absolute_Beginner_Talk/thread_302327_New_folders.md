---
title: "New folders?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Scotch on 2006-11-18
Okay, This is how things are now.. I can now open my hard disks and use the stuff on them, but how can I create new folders in them?

_Scotch_

---

### Post by redbluemangle on 2006-11-18
open the in your file browser and right click on an empty spot, options are in there.

---

### Post by PPAAUULL on 2006-11-18
That is if it is a linux drive or a fat32 file system. If it is a NTFS drive then you can't write anything on it without certain programs.

---

### Post by Scotch on 2006-11-18
> **PPAAUULL said:**
> That is if it is a linux drive or a fat32 file system. If it is a NTFS drive then you can't write anything on it without certain programs.

explain that deeper?:-k 

I've tried right clicking, but it is just grey options there](*,)

---

### Post by celsofaf on 2006-11-18
Your other hard drive, is it NTFS formated? If so... yes, no way to do what you want.

---

### Post by Scotch on 2006-11-18
I haven't done anything with my hard disks:???:  

I don't get the problem that I have with my hard disks:-k

---

### Post by nekr0z on 2006-11-18
Allright, let me explain it a little.

You see, in order for Operating System to know what information is there on the disk and how it is arranged in files and folders, there is what we call a Filesystem on every disk (or part of a disk that you see as a separate drive). And there are different filesystems, designed for some reason each. You can actually google for differences and comparing the filesystems, if you are interested.

The thing is, in Linux we generally use filesystems like EXT2, EXT3 (this one is most common, and default for Ubuntu), ReiserFS, HFS and like. In Windows world FAT32 and NTFS are generally used (NTFS in Windows XP native and default).

You can guess these filesystems are not compatible. Thank gods, Linux can read files from nearly any filesystem in the Universe. But reading files is not too hard, harder is to write new files to filesystem without breaking it.

This is where your problem seems to be: you are trying to create a folder on a disk with NTFS filesystem (it probably came from your XP). Linux has only experimental support for writing to NTFS, and trying to do this you have good chances to destroy your NTFS completely. To save you from despair, all the operations to create, write or otherwise modify an existing NTFS filesystem are prohibited in Ubuntu by default, so NTFS remains for reading only.

---

### Post by Scotch on 2006-11-18
So if I re formate those hard disks that I can't write on it will work?

---

### Post by unbuntu kid on 2006-11-18
I advise creating a seperate FAT32 partition using some partition program.  Linux and windows both understand and can write in this format.
Note: the live CD has a partion editor, although I haven't a clue if it is non-destructive.  You CANNOT edit partitions within a hdd os!
Good luck!

---

### Post by nekr0z on 2006-11-19
It works if you reformat the partition into EXT3 (or at least FAT32), but you lose your data while formatting. The solution here would depend of what you want to get: do you want Windows still working, do you want that drive we are talking about to be accessible from Windows, etc.

---

### Post by Scorpuk on 2006-11-19
Where abouts are you trying to create the new folder?


If its not in your home directory then you do not have permission to create a new folder there. (Why the options are greyed out)


As a security measure ubuntu will only allow the user to create / delete / modify files or folders within his or her own home directory. ie:

/home/john/   


To create a folder elsewhere you need to switch to a superuser. This can be done in two ways:

1. Terminal

```
Sudo su
```
(Type in main user password here - will not be displayed as you type: security measure)

Use cd to change folders and ls to list what is in current folder to navigate to where you want to create the folder.

```
mkdir <directory name>
exit
```

Exit is used so that you are no longer a superuser after using the mkdir comand.


2. Graphical

From a Terminal window type:

```
gksudo nautilus
```

You will be asked for the main user password again.

After that nautilus, your file browser, will start and you will have superuser (admin) rights



[B][I][U][INDENT]WARNING:

Deleting the wrong file as a superuser can bring down your system. Do be careful!!!!!![/INDENT][/U][/I][/B]

---

### Post by Scotch on 2006-11-19
I'm the only user on my computer and I can't create folders on any of my hard disks:neutral: 

I don't get this EXT3 (or at least FAT32):-k 

Scotch

---

### Post by Scorpuk on 2006-11-19
You may be the only user on the computer, but ubuntu will restrict access to all other folders apart from /home/<user>.


Only a superuser can add folders / change files etc outside this area.


This is to prevent the user from mistakingly doing somehting to the core files and the system never working again.


When you install ubuntu the password you assign to the user you create is assigned to the superuser too. So anytime you use sudo the password it requires is the same as your own password.


try this:

open a terminal window

```
cd /
mkdir test
```

now try this:

in a terminal window type:

```
sudo su
<type in your password and hit enter : NB you wont see anything onscreen as you type>
cd /
mkdir test
```

In the second example you should not get any error messages about permission, unless you typed the password in wrong. ;)

---

### Post by Scotch on 2006-11-19
I did what you said, but there is no changes:???:

---

