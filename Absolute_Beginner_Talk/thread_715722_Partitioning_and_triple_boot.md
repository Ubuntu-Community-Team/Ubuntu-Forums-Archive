---
title: "Partitioning and triple boot"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Kiri on 2008-03-05
Hi,
I'm just about to (try) and get into using linux and joining the linux community. 

I've been doing a lot of research about different distros and how to go about dual booting linux with Windows XP. 
I'm finally starting to get my head around it, but have a few specific questions, and generally want to check if I'm on track.

For the linux distros, I've narrowed it down to 2 actually: Mint 4 (or Ubuntu 7.10) and PClinuxOS 2008 Minime.

Current OS is XP Pro sp2.

I have an 80GB HD partitioned like this
-Primary Partition-
C: (XP System only) - 8GB

D: (Program Files) - 16GB
E: (Data) - 40GB
Z: Swap - 2GB

All are formatted to NTFS. 

My plan is to delete/reformat the DATA partition (40GB) and use it for linux. 


So my question is:

How should I repartition that 40GB of space to be able to install 2 different distros and triple boot with windows?

Also, do the partitions for the linux OSs need to be primary? (some guides say yes, other say extended is fine)



I will probably end up using one of the distros as my main one, and probably the other partition to test other distros in the future, so the 2nd one could be a smaller partition I guess.

So I'm thinking something like this:
6GB for Ubuntu or Mint
4GB for PClinuxOS (too small?)
2GB for linux Swap file (I have 1GB physical RAM)
28GB for Data (formatted to Fat32 to be compatible with windows)


Does this some appropriate? I'm also open to any other ideas, but I only have the 40GB of free disk space to play around with... 

I read something about being able to install programs to a separate partition and use them in different distros, but I didn't quite grasp it. (the linux file/directory system or root, home, etc is still really foreign to me)

By the way, I don't suppose I can use my windows Swap partition for the linux swap files too can I? 



Thanks in advance for any help. I'm really eager to get involved with linux.

---

### Post by 10Digits on 2008-03-05
First of all Welcome TO UBUNTU !!!!!

You might just want to check out the live CD first....

Also, I think u should check out the following URL < Oedha really helped me out !!!:guitar:>

[http://ubuntuforums.org/showthread.php?t=706983&highlight=Partition+jungle](http://ubuntuforums.org/showthread.php?t=706983&highlight=Partition+jungle)
:)

---

### Post by hoges on 2008-03-05
Well, for starters I'd recommend that you try the live cd (if available) of each distro first. Much easier than installing.

If you still want to go ahead with tri-booting, then here's a couple of tips (from painful experience):
1) Try to avoid using extended partitions. Unlike windows it is possible (I've done it), but it can become a huge mess, and you can spend a lot of time playing around with GRUB to get it right.

2) Ubuntu 7.10 comes with NTFS support out of the box. No need to stuff around with fat32 partitions any more. I can't guarantee any other distros, but support can be added to others. I was under the impression that it was in the kernel these days, but don't quote me on it.

3) I believe it is possible to share the home folder between distros, but I've never had the need to do this. Theoretically it should work, but I have no idea as to the reliability of it.

4) BACKUP EVERYTHING BEFORE YOU START!!!!! (again, painful experience).

One thing I'm confused on, though - what's that swap drive doing there? I was under the impression that the windows equivalent just used c: drive's spare space? I've never noticed one on any of my installs...

---

### Post by rolnics on 2008-03-05
First things first, make sure you've got backups of you data that you want to keep before you do anything else! 

I'm not sure about PCLinux's recuirments for space, but 8Gb for Ubuntu or Mint's / (root) partition would be best. 

Your swap partition is spot on, I don't think it can be used by windows, but I'm sure one of the other guys will correct me if i'm wrong.  

Otherwise I think you've got it sorted and welcome to Linux

---

### Post by rolnics on 2008-03-05
> **hoges said:**
> One thing I'm confused on, though - what's that swap drive doing there? I was under the impression that the windows equivalent just used c: drive's spare space? I've never noticed one on any of my installs...

It's like linux it can be more efficient to force windows to use a fixed amount for a swap file.

---

### Post by hoges on 2008-03-05
Heh, what do you know, I never thought that was an option...

I guess you learn something new every day!

---

### Post by Kiri on 2008-03-05
Thank you for the warm welcome and information :)

I have checked out the live CDs already and I like them, but I think I can't really get to know the system until I install them. So I figure I should just do it :)

So after that information, I guess I should keep the partitions for linux distros to be primary, and then extended for the other partitions. 
And I don't need to use a Fat32 partition for data to be accessible in both windows and linux? So then what file system should I use for my data / files partition?

Sorry for this basic question, but what IS the home folder on a linux system and why do some people put it in a separate partition?


hoges: To answer your question about the windows swap partition, yes windows defaults to just use the space on C drive. But I made my own partition for swap because it is often written to and I was thinking it would help my system from becoming too fragmented and also help system stability and performance. Also that way I can keep the OS in its own partition. I'm not sure how effective this is in reality, but it keeps things cleaner I think.

Thanks again

---

### Post by rolnics on 2008-03-05
> **Kiri said:**
> 
Sorry for this basic question, but what IS the home folder on a linux system and why do some people put it in a separate partition?


The home partition is like your current partition you have for data / programs.

---

### Post by Kiri on 2008-03-05
Thanks, I see.

I think I pretty much have the partitioning plan sorted out, but I'm wondering now if I might run into problems with the boot loader if I try to triple boot...

---

### Post by hoges on 2008-03-06
Nah, grub handles it all. I've got 3 os's installed, and grub handles them all brilliantly.

In terms of file system, just use the linux defaults for the partitions that linux is installed on, but keep in mind that you can only view windows partions in linux, but can't view linux partitions in windows.

---

### Post by oedha on 2008-03-07
based on mine....i ever install quad boot at that time.....1 xp + ubuntu + fedora + suse 
primary for win....and the rest in the extended.......i didint make data or home partition....( i just want to test....)
the main point is : "**partition**"
and you have all the answers.......happy partitioning :)

---

### Post by angry_johnnie on 2008-03-07
Just one more thing to add here.  If you're going to install more than one Linux distro, I would suggest installing Ubuntu or, in your case, Mint, at the very end.  The reason for this is that PCLinuxOS will install Grub and recognize your windows installation.  But it won't recognize other Linux systems you may have installed before, which means you'll have to add them manually to grub's menu.list.  Ubuntu, on the other hand, is much more polite.  It will recognize every OS you have and add it to GRUB's list.  I have six operating systems on my main PC, and Ubuntu recognized all of 'em.  It just makes everything easier :-)

---

