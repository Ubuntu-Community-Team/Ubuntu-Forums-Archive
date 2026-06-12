---
title: "Partitioning problems"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-06-20
So I had a HD that I was goofing around with, and it now has Ubuntu server installed. But now I'm converting it to an external drive. It wouldn't show up in Windows, so using the Xubuntu Live CD, I can see the hard drive, it has the right amount of memory, etc. But, when I fire up the Gnome Partition Editor, that disk is off-limits because it's accessible only by root. I want to format the whole thing in NTFS (unless you all think I should do it otherwise), but I can't do anything to it from the GUI tool. I'm comfortable with the command line, I just don't know what to do. Help?? Thanks.

---

### Post by JebusWankel on 2007-06-20
Unless you'd prefer a command line tool, running "gksudo gparted" should give you the root access you need.

---

### Post by arvevans on 2007-06-20
In terminal mode you could use:
[INDENT]sudo fdisk /dev/<drive_identifier>[/INDENT]
Fdisk in Linux has commands that are not available in the Windows version of Fdisk, so read the "m" help screen to see what to do.
_._

---

### Post by chimerical_brio on 2007-06-20
Whoops, sorry for the previous bump, I didn't see the replies.

---

### Post by Clay_Banger on 2007-06-20
you could also use the gparted live cd, similar to using xubuntu live cd then sudoing gparted, but it loads quicker and its main purpose is to format/move/resize/delete partitions.

---

