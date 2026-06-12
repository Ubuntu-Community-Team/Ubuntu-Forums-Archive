---
title: "Mounting Errors"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by MattMalone on 2007-04-13
OK, I am 10 minutes into using the Live CD of Ubuntu. Trying to mount my C: so I can see how easy integration would be with my current work files. I get this error message when I try to access it through the computer screen

error: device /dev/hda1 is not removable

error: could not execute pmount

Cheers for your help.

---

### Post by devnulljp on 2007-04-13
What are you trying to do? 
try this:
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ****

where **** is one of vfat or ntfs depending on the filesystem of your C: drive

Then you should be able to cd /media/windows and see all your old files.
That help any?

If that doesn't work, post the results of 
fdisk -l

---

### Post by MattMalone on 2007-04-13
OK, I am very much new to the terminal concept. And I am totally lost lol.

What I want to do is, in windows speak (I'm sorry if I offend) is access my C: using the live CD so we can test out some of our applications.

---

### Post by devnulljp on 2007-04-13
So, you need to do what I wrote above to mount the partition. 
boot from the cd
at a terminal (it's just like dos) type:
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ****

where **** is one of vfat or ntfs depending on the filesystem of your C: drive
and windows is on the first partition of the first IDE hard drive (it will probably be something like sda1 if its SATA or SCSI). 

then 
cd /media/windows

You should now be in root of your C:\ drive.

Or you can then go in with a graphical file manager; just type /media/windows in the URL bar.

---

