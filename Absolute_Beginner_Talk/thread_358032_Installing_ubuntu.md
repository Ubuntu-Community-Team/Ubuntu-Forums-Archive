---
title: "Installing ubuntu"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by xRedlinexx1 on 2007-02-10
I just recently decided i would try linux, so i chose to use ubunto. I downloaded the iso and put it on a blank cd. Then i booted it up. Now i want to actually install it on my hardrive using the install tool on the desktop. My problem is i dont understand what to do with the partioning. I would like to install ubunto only on my d drive(which is a backup drive i dont use) and leave windows untouched on my main c drive. How can i do this and what kinds of mount points should i be using.

Thanks, Eric

---

### Post by NeoGreen on 2007-02-10
Is this a secondary HDD or is it a partition within your C drive?

---

### Post by mozkaynak on 2007-02-10
try this:

[http://ubuntuforums.org/showthread.php?t=16287](http://ubuntuforums.org/showthread.php?t=16287)

---

### Post by NeoGreen on 2007-02-10
When you get to the partition part, do you see D drive on it?  If you do you can select it and then let it partitio automatically for you.  This may require erasing any data on D drive then installing the Ubuntu to it.

---

### Post by NeoGreen on 2007-02-10
mozkaynak, outstanding link.  I was searching for that one earlier.:)

---

### Post by xRedlinexx1 on 2007-02-10
At the start of the partitioning steps it asks me if i would like to reformat all of the space(or something like that). The second option says something about continous free space, and third option says modify partions. I chose modify partitions because the others said that would reformat or something. Inside here it lists 2 ntfs partitions and a fat32. The smaller ntfs is the d drive. Do i resize it to nothing then make partitions out of the free space? If so how many partitions do i need and what mount points in the next step?

(EDIT) I just took the second ntfs and made an extended partition. I then made two ext3 partitions in it. I'm am currently installing ubuntu.

---

