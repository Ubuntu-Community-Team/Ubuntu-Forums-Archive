---
title: "hard drive too small, partition too big"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by thetechgeek on 2007-04-15
I am currently running ubuntu on a live cd, and I need to install it. There's only one problem- MY HARD DRIVE IS TOO SMALL AND THE MAIN PARTITION HAS LOTS OF EMPTY SPACE!!! I cant resize the main partition. I still want windows to run (well, duh, I paid for it...) and I want a dual boot situation at startup. What would be the proper way to backup the partition(How do i figure out whats in it) and how would I make a new partition like the old one, except smaller so I can have room for linux(and so windows would still work)??????????
:confused: :confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by BoneKracker on 2007-04-15
search in the forums for "resize ntfs partition"

---

### Post by K.Mandla on 2007-04-15
If I understand your question correctly, you might be able to resize your partition with something like GPartEd. It runs as a live CD and can usually handle anything you throw at it. Take a look [here]("http://gparted.sourceforge.net/livecd.php").

---

### Post by thetechgeek on 2007-04-15
that's what came with the installer. I have a type fat-32 main partition (only one hard drive), and you can't resize that, am I correct? The only way I can think of to get space would be to back up that partition, delete it, create a new, smaller partition, and put back the old stuff. How can I do that with windows still working so I can do a dual boot???
(NOTE: the main partition doesnt have the tag "boot". a much smaller partition does.)

---

### Post by freebird54 on 2007-04-15
If you have empty space within the partition, GPartEd can resize without problems.  Resizing VFAT and NTFS partitions is one the main reasons for its inclusion in the installer.  The best procedure is to boot Windows, turn off the Page File (right-click My Computer select Properties.  If it is a laptop, kill the hibernate file too.  The run defrag a few times (3 should do it).  Now you will have as much empty space as possible for other uses, and getting it resized to your specs will be no problem.  The installer can even do it automatically, if you don't want to decide...

EDIT:  Almost forgot - it is SAFER to back up before resizing.  I haven't heard of it happening, but things COULD go wrong.  If you have a backup, Murphy's law says nothing WILL go wrong :)

---

