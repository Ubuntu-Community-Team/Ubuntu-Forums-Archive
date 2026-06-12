---
title: "External hard disk wont partition"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by flavio newbie on 2007-03-11
How do i do a partition of my external usb hard disk?
its in nfts now, but it wont divide into two partitions...
Im a real beginner, please help me

---

### Post by laidback on 2007-03-11
Suggest you run Gparted. It's in System>Administration>Gnome Partition Editor.

Now one thing you need to know, you cannot play with (partition) on a mounted drive. I suspect that Ubuntu mounts your USB hd by default. (i.e. you can read the directories from within the file manager etc). In order to repartition or reformat a drive it must first be unmounted. Gparted has an option to unmount the drive. Do that first. Your main hd should be left mounted (probably called hda1 ).

Just view and get the hang of what you could do first off, before committing to soemthing serious.

Oh and Welcome to Ubuntu.

Laidback

---

### Post by flavio newbie on 2007-03-11
ok, now that i unmounted the option format is not gray anymore, but if i format, can i format only half of it? and if yes how, because i have 35 gb of files on it, and i dont know where to put them

---

### Post by laidback on 2007-03-11
Please see here for more info and directions:-

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Basic idea:-
If I remember correctly, select the drive via drop down top right. Click on partition within the body of the window. Now you should see resize/move become available, obviously you need to reduce the size of the existing partition before you create a new one. Assuming you have insufficient space left. The diagram of the hd gives you the info on that. Grey area to right is unallocated/unformatted space.
However, please note that I haven't done this with an ntfs partitions myself, I've only used the Linux types. I have read that for ntfs you should run the Windows programs that sorts out hd first. Cannot remember its name, but it compresses the files to the LHS of the picture display, I think you'll find it in Control panel. I also suggest that you back up your data first, messing with partitions can be risky. 35Gb takes some backing up but I strongly advice you to do it.

Please read the Gparted HTML or pdf file first.

---

