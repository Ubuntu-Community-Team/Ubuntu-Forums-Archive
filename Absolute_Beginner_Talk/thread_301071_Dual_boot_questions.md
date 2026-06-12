---
title: "Dual boot questions"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Taskman on 2006-11-16
I am very much a beginner so I just want to make sure I am doing this dual bot thing correctly.  I have a 250 GB hard drive with one small partition for raid and the rest is one big blank partition.  

Question #1:  As I understand , it is best to install XP first.  So, should I create a separate partion for XP and Ubuntu before I install XP or should I just go ahead and install XP on the whole hard drive and then create another partition when installing Ubuntu.

Question #2:  After both OS are installed is it possible to change the partition sizes or add new partitions.

Questions #3:  Is there a reason (advantage) to have a seperate partition, apart from the OS, for video and pictures etc.

Thanks in advance

---

### Post by to4i on 2006-11-16
#1. It's up to you.
#2. Yes
#3. It's better to have a seperate partition to store files, cause after preinstalling XP you won't loose them.

---

### Post by jimbob on 2006-11-16
1)  Personally, I would create an NTFS or FAT32 partition as the first one on the drive and let XP use that.  Sometimes XP will seize the entire drive and you definitely don't want that. Ubuntu is smart enough to use what is left for itself and generate a dual boot system for you.  If you have Ubuntu first  XP will call that your C: drive and you may end up with a system where the XP partition is called F: ( it will still work but can cause real pains later ).

2)  Yes, Gparted.

3)  I don't, but then I have nothing that I particularly care about losing in case of a crash and burn.  If you do, then yes.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by alchimera on 2006-11-16
I suggest that you have a look at this: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
and plan your partitions carefully before you do anything!  There's more good advice available too, have a look about (Google it!).

You are probably best to install XP first, and then when you install Ubuntu the grub boot menu will get configured so you can dual boot easily. 

Good luck and have fun :-D.

---

### Post by Henry Rayker on 2006-11-16
Personally, I would suggest:
Install Windows on a NTFS filesystem first. Keep that partition for all of your programs and the like. 

Make a FAT32 partition for data (so it can be easily shared/read/written by both OSes...Ubuntu doesn't play too nice with NTFS, IIRC).

Install Ubuntu on the ext3 and make the swap partition.

As for resizing/creating new partitions, it is possible, you just have to be careful/back up before doing it. I've never had a problem with resizing my windows partitions, but I'm lucky, I hear.

The "Separate Data from OS/Programs" policy is one I abide by on ANY windows system I set up. I prefer to even keep my data on a separate physical drive, if possible. I've had too many Windows installs completely eat the drive they were on.

---

