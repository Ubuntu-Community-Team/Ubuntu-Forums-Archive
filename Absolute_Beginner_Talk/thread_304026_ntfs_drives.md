---
title: "ntfs drives"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Padraig Notlad on 2006-11-21
I am new to Ubuntu.  I have read a lot of info on getting read/write access to ntfs drives.  I'm pretty confused still.  I have installed Ubuntu on a 3rd HD in my computer.  I have a RAID 1 setup for Windows XP.  I have lots of files on my NTFS drives that I would like to just copy over to Ubuntu.  I don't need to write to them, just read.  I seem to be able to see them and they say they are accessible from Disk Manager, but when I try to access them I get a message "you don't have permisssion" etc.  I thought it was easy to do this?  When I was told about Ubuntu, one of the usefull things a friend was telling me was that booting from the CD was cool because you could recover files from a bad Windows system using a jump drive.  Not exactly what I want to do, but I would think the process is similar.  Anyway, can anyone give me an explaination in laymans terms?

---

### Post by hyper_ch on 2006-11-21
If you see them on the ntfs drive in ubuntu then you can also ocpy them :) are all those files in one place? If so you can go to the command shell and copy the files as root and then chown the files to your user.

e.g.

mkdir /home/youruser/Desktop/windows

su cp -R /path/to/ntfsdrive/path/to/folder/* /home/youruser/Desktop/windows

su chown -R youruser:youruser /home/youruser/Desktop/windows

---

### Post by housam on 2006-11-21
you have to mount your ntfs partitions first and then you can access it.
try this link :
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) 
item 14 
good luck

---

### Post by hyper_ch on 2006-11-21
he said he can see them so I assume he has already mounted the drive

---

### Post by anaconda on 2006-11-21
Does it work if you start nautilus with root rights?
```
gksudo nautilus
```
opens nautilus with root rights.

---

### Post by housam on 2006-11-21
I may be wrong but the uncompleted error message shows that the partitions are not mounted yet.:confused:

---

### Post by Ben Sprinkle on 2006-11-21
[Click here to find out how to read/write to NTFS partitions.](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Padraig Notlad on 2006-11-21
anaconda...

You rock!  That worked!  Thanks for the help everyone!
I am liking Ubuntu.  It's been fun so far.  Only been using it for 2 days, and I'm impressed.  Sharp learning curve though.

---

### Post by Ben Sprinkle on 2006-11-21
> **housam said:**
> you have to mount your ntfs partitions first and then you can access it.
try this link :
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) 
item 14 
good luck

You can access it meaning read (copying), but you cannot write to it.

---

### Post by Robert.Zapata on 2006-11-22
> **anaconda said:**
> Does it work if you start nautilus with root rights?
```
gksudo nautilus
```
opens nautilus with root rights.

Hello Team:

I'm having the same issue with my external USB drives.

That solution is not working, the HD still shows as read-only, I can copy files **from** the HD but not **to** it.

I guess I'll have to change it to FAT32.

---

