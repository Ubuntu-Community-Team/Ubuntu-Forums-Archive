---
title: "Partition and Installation Advice"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Twisthem488 on 2008-02-08
Hello, I'm waiting to install Ubuntu, but I need some help first. I have no idea what I'm doing with these partitions.

I'm currently running Windows XP, and would like to set my system up to dual boot. I have 512 MB of ram, a 37 gb drive for program files (26 gb free), and a 110 gb drive for all my other files (25 gb free). Both are NTFS.

I would like to have both Ubuntu and XP run from the 37 gb drive, and would like to again, keep all my misc files on the larger HD. 

I have made 2 passes of defragmentation on both drives. When I go through the partition segment I am presented with the following options:

1. Guided - Use entire disk (both drives are then listed)

2. Guided - Use the largest continuous free space

3. Manual

Am I correct in thinking I would want to use the second option? When I try this I am told that I failed to partition the selected disk, and that its probably because the free space is to small to be partitioned. 

After this happens I am given to more options.

4. Guided - Resize IDE1 slave

5. Partition #1 (hdb1) and use freed space

From there I assumed that I would want to use option 4 to resize the current partition on my drive, and add one for linux, but I am presented with this:

[IMG]http://i29.tinypic.com/2wc2sky.jpg[/IMG]

Some questions.
1. What process should I do in order to setup linux on my 37 gb drive alongside xp, so that it can boot with xp.

2. What is swap.

3. What is NTFS, and how does it affect my system

I'm looking forward to getting this up and running, and will actually be donating this machine to my parents sometime in the near future. Thanks in advance for any help :D

Joseph

---

### Post by Daveski on 2008-02-08
> **Twisthem488 said:**
> Some questions.
1. What process should I do in order to setup linux on my 37 gb drive alongside xp, so that it can boot with xp.

2. What is swap.

3. What is NTFS, and how does it affect my system


In Linux your virtual memory - or swap area, is a dedicated partition (usually), whereas in Windows land, this is a file stored by default on your system drive called pagefile.sys. You need a small swap partition for things in memory to be swapped to. This should be between 512Mb and 2Gb in your case.

NTFS is Microsofts proprietory disk filing system. You might know FAT, FAT16 or FAT32. NTFS is the newest and most secure disk filing system for NT / 2000 and XP (possibly Vista). Ubuntu will use EXT2 EXT3 or some other filing system. The upshot is that if you want to access NTFS volumes such as your Windows partition in Ubuntu, you will need an NTFS filing system driver (which is included), but bear in mind that this is a reverse-engineered driver to access a proprietory filing system and as such does run the risk of damaging data on this volume (although I have never seen this happen).

---

### Post by Pharoz on 2008-02-08
Try this thread. It's what I currently use and and may be what you need to set this up...

[http://ubuntuforums.org/showthread.php?t=687861](http://ubuntuforums.org/showthread.php?t=687861)

---

### Post by Twisthem488 on 2008-02-09
Ok, I've played around with it more this morning and found out what got me confused. I was thinking that the ubuntu installer would set up all the partitions for me, and was wanting to know which option would do that. Now I realize that i need to use the Partition editor, and then use the installer. The problem I'm running into though, is that gparted wont let me resize my partitions. I made sure they are unmounted, but for my 37 gb drive, it says the minimum size is the same as it is, and for my 110 gb drive it says it can only be 8mb smaller than it already is. Why wont it let me partition it more?

My only thought is that there are files that extend to the end of the drive, even though my drives arent full, so as I wait for a reply I'll log back into windows and run some more defrags.

---

### Post by Twisthem488 on 2008-02-10
Heres a screen capture of what I'm talking about. It wont let me resize the current partition, meaning I cant add another one.

[IMG]http://i25.tinypic.com/dnc5l5.jpg[/IMG]

---

### Post by zvacet on 2008-02-10
Download [Gparted live Cd](http://gparted.sourceforge.net/) and burn it on disc and boot with it.With that tool you will be able to do what are you planing.

---

### Post by Twisthem488 on 2008-02-10
I just tried the gparted live cd without any luck. It makes sense that it provides the same results as I was getting, because gparted is what I was running off of the Ubuntu live cd. 

My current situation still stands. My minimum partition size is the same as my maximum size, meaning I cannot shrink it, and add another partition for Ubuntu. Any more ideas would be greatly appreciated. 

Joseph

---

### Post by Moop on 2008-02-10
You need to click on and highlight the partition and then the resize option will be available.

---

### Post by Twisthem488 on 2008-02-11
@Moop:

I am doing this. Thats how I get to the screen I was at. If I dont select/right click on the partition I dont get the resize options at all. The problem is that I do get the option, but the minimum partition size is the same as the current size. So I have the feature available, but it wont do anything. 

I've found a similar problem in [this thread](http://gparted-forum.surf4.info/viewtopic.php?pid=1978), but I cant make enough sense of what he did to fix the problem to try it out for myself.

---

### Post by Daveski on 2008-02-11
You say you have defragmented the NTFS partition in Windows - yes? Have you also run a chkdsk /f on this drive (from Windows)? Also make sure you have actually shutdown Windows, not hibernated it.

---

### Post by Twisthem488 on 2008-02-12
I have indeed partioned my drive in windows. I took your advice and ran a chkdsk, which is something I had not thought about. It came up with some small things that it fixed, and yet I still have the same problem.

I'm sure I'm shutting down  windows. There was one instance where I didnt shut it down properly, and the drives were still being associated with windows, but other than that I'm nearly positive I'm going through this correctly. Alas, alack, I ere to be human, and as such am laible to mistake. 

I'm sure this is seems as tedious to you guys as it does to me, and i thank you again for staying with me in an attempt to get this working.

Joseph

---

### Post by Forrest Gumpp on 2008-02-13
Twisthem488,

Have you looked at this thread:  [http://ubuntuforums.org/showthread.php?t=687630](http://ubuntuforums.org/showthread.php?t=687630)  ?

There may be a related issue to your seeming inability to shrink your 37 GB partition.  Forum member rkd gives some incredibly detailed help to user thinch in this thread.  I only posted there trying to be helpful because I had heard about an immovable files issue relating to XP.  I lack the knowledge to explain it further.  I just get a sense that your issues and user thinch's may be similar.

It appears from his last post that thinch's issue was resolved.  Might be worth a look if you have not already done so.

---

### Post by Twisthem488 on 2008-02-14
I'm off to classes, so I'll have to look at it later, but thanks for the link Forrest! I talked with someone last night and they too thought it might be because I could have unmovable program files on one side of the partition and said he would give me a copy of a partitioning tool that would be able to congregate all the files together.

---

