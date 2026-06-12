---
title: "Creating a partition on one of two hard drives"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Bisqui[c]k on 2007-06-27
Hi, I'm new to Ubuntu and I have a problem.  I've searched through the various how-to's and forum posts and I haven't found an answer to my question, so here goes.

I have two hard drives.  One is 80 GB and the other is 250.  I have a fresh Windows XP Pro installation on the 80 GB drive.  I've just used the 250 GB drive for media storage and to backup files.

The 80 GB drive is partitioned into one 76 GB partition and one 4 GB partition (that came with the computer, it's for recovery).

My goal is to dual boot XP and Ubuntu.

My problem is that when I install Ubuntu (graphical install of the latest version) it does not give me the option to add a partition to my 80 GB drive and install Ubuntu on that.  It simply gives me the options of 

1) a guided resize of the partition and install on the 250 GB drive 
2) a guided format/install on either of the drives
3) a guided "use the largest contiguous free space" (which happens to be on the 250 GB drive
4) manual

How can I go about getting Ubuntu installed on my 80 GB drive?  Thanks for your help :D.

---

### Post by kevinlyfellow on 2007-06-27
If your not constrained with ram, I suggest installing gparted.  Just open up the terminal (Applications -> Accessories -> Terminal) and enter the following command
```
sudo apt-get install gparted
```

Use that to make some freespace and choose option 3

---

### Post by Bisqui[c]k on 2007-06-27
Thanks, I'll give it a shot and report back.

---

### Post by Bisqui[c]k on 2007-06-27
It worked, thanks a million!

---

