---
title: "Accessing/Formatting Secondary Hard Drive"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by eyesrglazed on 2007-05-03
Well, here's my problem. I've tried using Ubuntu before, and it crashed after I had obtained nearly 50GB of videos through BitTorrent. Then my computer crashed, and I had to reinstall stuff on it.
I now have what I think is a solid install of Fiesty on my 40GB hard drive, and I wish to be able to save my files on the 2nd drive, a 120GB Maxtor. My only problem is that I don't know how to access it, or how to format it. It seems like my computer is having issues recognizing it and accessing it.

I should be able to get to it in the file system through the /media/ folder,  shouldn't I?

What I'd like to do is wipe the 120GB, and format it with the ext3 filesystem or whatever, and be able to save stuff on it while I'm running Ubuntu off of the other drive.

---

### Post by taurus on 2007-05-03
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Or you can use gparted, System -> Administration, to format your second harddrive to ext3.  Then, you would add an entry in /etc/fstab so that it would be mounted each time you boot Ubuntu.  And to be able to write to it, you just need to change the ownership of the mount point for the second harddrive from root to whatever your log in name is.

---

### Post by eyesrglazed on 2007-05-03
Well, I've formatted the hard drive... How do I add the entry to /fstab/?

Also, if I'm the only user on this computer, do I need to change the permissions for the hard drive to write to it?

---

### Post by taurus on 2007-05-03
Can you post the output of these two commands?  Then, I can walk you through mounting it (from /etc/fstab) and changing the ownership of that new harddrive so you can write to it.

```
id
sudo fdisk -l
```

---

### Post by eyesrglazed on 2007-05-03
Strange... Terminal won't run from the menu. Where would the actual program for that be located?

---

### Post by taurus on 2007-05-03
Applications -> Accessories -> Terminal or <Alt>F2 -> gnome-terminal.

---

### Post by eyesrglazed on 2007-05-03
Well, apparently Terminal won't run.

Since my install is pretty recent, if there's a way to set up that drive while installing Fiesty, I could reinstall if you gave me instructions... Like when I get to the partitioner section, since I'm assuming you can do something like this at that point.

---

### Post by eyesrglazed on 2007-05-04
Let me try re-wording my previous question. While installing the operating system, is it possible to set my second hard drive up so that Fiesty is installed on the first drive, and can access the second for storage?

---

