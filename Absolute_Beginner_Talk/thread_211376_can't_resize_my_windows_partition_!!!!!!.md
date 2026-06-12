---
title: "can't resize my windows partition !!!!!!"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by blunile on 2006-07-08
[B]i'm an absolutely newbie and need to use ubuntu with win xp .

I can't resize my windows partition (too samll) ,and want to dual boot ubuntu ,IT seems too difficult.

I can't mount partitions (don't know what that means) ,I can't install ubuntu on a different hard disk ( a smaller secondary 40 gb)......when I select hard disk 2 and order it to completely erase it , the installation crashes on last step-during copying files- and tell me to report a bug !!!

[B]How to dual boot ubuntu on a 30 g hd on a differnt partition than that of windows ???
 
Can some body help me please ??

---

### Post by Crosbie on 2006-07-08
Are you using the new 'Dapper Drake' Ubuntu LiveCD to do this?  Does the LiveCD work okay?  Otherwise, what installation method are you using?

How many drives do you currently have?  How many partitions on each drive?  What's on 'em?  Give us a list.

---

### Post by jan on 2006-07-08
You can try doing the partitioning work with Knoppix live CD. It has a tool called Qparted (or Qtparted, not sure now) and It usually has no troubles with any of the partitioning.

---

### Post by catlett on 2006-07-08
Try to format ahead of time. (you have to know how to burn an ISO and boot to a live CD to do this. I am going to assume you can because you have created the install disk and have booted to it)
Anyways download and burn this ISO to disk [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) This a partitioning application.
The simplest thing you can do is delete the partition or partitions on it.
Then when you go to the installation it will see the unallocated space and ask if you want the install there.

Or you can format the partition into 2 partitions. One a small 512MB (actually the rule of thumb is twice your ram i.e. 256 MB ram = 512MB ) partition formatted as Linux swap. The other partition will be whatever is left for space.
Then the installer will put the program files on the ext3 and will use the Linux-swap as swap. (swap is virtual memory. windows uses a file  while Linux uses a partition.

Hopefully that will help. If it doesn't, the CD may have been corrupted during download or burning. In that case you will have to create another install disk (FYI  you should burn at 4x speed or even slower to avoid errors when  burning.)

---

