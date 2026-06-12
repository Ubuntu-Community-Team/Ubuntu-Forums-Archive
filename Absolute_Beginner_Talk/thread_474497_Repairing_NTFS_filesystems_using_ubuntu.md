---
title: "Repairing NTFS filesystems using ubuntu"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by joe_aule on 2007-06-15
I was using Partition Magic to resize my existing NTFS partion I run XP from in order to install Ubuntu in a seperate partition. However, partition magic chose to crash mentioning errors with file attributes but due to a bad memory and the fact I never thought to write it down at the time I don't have anything in particular to google for. 

Right now, I cannot boot windows and I cannot install Ubuntu . The Gnome partition resizing tool (I ironically discover afterwards) says "Failed to fork (cannot allocate memory)" and when I try to mount the drive (which was previously possible), ubuntu says "wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error".

Is there any way I can recover the data on the drive by fixing the partition?

Thanks in advance for any help and advice.

--edit--
Found the syslog utility and these two lines seem relevant:
NTFS-fs error (devices sda1): load_system_files(): failed to load $Bitmap
NTFS-fs error (devices sda1): ntfs_fill_super(): failed to laod system files

---

### Post by Cappy on 2007-06-15
There is a program called testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

```

sudo apt-get install testdisk
```

If you *do* try using it and it finds errors that it can fix, be sure to use the option to backup whatever the program lets you *before* you commit any changes. Obviously, you need to think things through before you commit any changes with this program or else it could make the situation worse.

---

### Post by Herman on 2007-06-15
Download a copy of the latest [GParted -- LiveCD]("http://gparted.sourceforge.net/") and burn it to a CD disk.

Boot your computer with GParted Live CD, open a terminal in GParted and type 'testdisk' in it. 
Here is an illustrated example of how to use TestDisk, [http://users.bigpond.net.au/hermanzone/TestDisk How-To.html]("http://users.bigpond.net.au/hermanzone/TestDisk%20How-To.html")  be sure to read it first and follow the links in it too. Then try TestDisk for yourself and keep your fingers crossed!
Good luck,
Regards, Herman :D

EDIT: It looks like Cappy beat me to it, you can use the Ubuntu installable version of TestDisk like Cappy said, and the advice about using the backup option is something I haven't looked into, it makes sense and you should follow that advice.

---

### Post by joe_aule on 2007-06-15
Thanks for the help. I've downloading the gparted livecd and am currently trying to find a way to burn it using my brothers computer.

---

### Post by Cappy on 2007-06-15
I wouldn't know anything about making a situation worse *cough*
If something *does* happen, here is an open source data recovery program:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It installs when you install testdisk =)
```
photorec
``` to run that data recovery program. You'll want to use testdisk first but I thought I would mention it just in case before you decide to give up and overwrite your disk with a new OS.

One last note, you'll need to make the make the terminal fullscreen before you run testdisk/photorec or else you will get an error.

---

