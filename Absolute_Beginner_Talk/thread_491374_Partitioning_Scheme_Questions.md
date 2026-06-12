---
title: "Partitioning Scheme Questions"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by EvilMarshmallow on 2007-07-03
Hey all,

I've been playing with Ubuntu since Christmas and really fell in love with it.

However, my beginner's ignorance has led to a real mess when it comes to my system.  Some things aren't working, and I can't figure out how to fix them... so I'm going to blow it away totally.  I don't have a lot of files saved on it, so they're easy to back up to CD and restore later.

My question is,  how can I set up my system to make it really easy to try new things, and not have to go through so much headache later when I have to blow it away?

I've read that having a separate partition for /home, /swap, and /boot are all good ideas... but I don't know enough about linux to set them up correctly.  Right now I have one giant partition.

Can someone walk me through setting up the partitions the best way?  I have a 160GB hard drive... allocate it however you feel is most appropriate (but tell me why!).  I'll be installing Kubuntu Feisty.

---

### Post by arvevans on 2007-07-03
Pull up a terminal screen and enter:

[INDENT]df -l[/INDENT]

From analyzing the output you should be able to tell how much space to allocate for something like this:

[INDENT]/boot

/home

/  (root)

swap[/INDENT]

Since you can only have 4 primary partitions on a hard drive, this is about all you can do without resorting to logical drive partitions.

By having a separate "/home" you can save or backup all your personal files from that partition.  

This may not be the optimum way, but it works for me.
_._

---

### Post by Raineer on 2007-07-03
Definitely don't need all 3 but yeah it's not a bad idea.
I use the first 2 gigs for swap (which is practically never utilized because it's very low priority in Linux, unlike windows).. Like 20 gigs for boot, though most recommend around 6-10.  The rest can be /home, most of your files.

If you want a tool to set it all up, google the Gparted Live CD which boots itself and can safely move/shrink/split/resize your partitions.

---

### Post by alex_anthony on 2007-07-03
maybe you should take an image of your system just after you get everything installed and configured, so you can restore it later instead of blowing it away. Maybe, if you have spare space on an external disk, think about imaging when you're going to make any big changes which could make you want to blow away your system. Then you try your new thing, like it delete the image, don't like it, restore the image.
Perhaps partimage

---

### Post by EvilMarshmallow on 2007-07-03
Thanks for some quick replies!

**alex_anthony:**
Not a bad suggestion... I'll definitely save my image once I get it done.  Even so, I'd like to separate the different functional areas, just in case the need arises one day...

**Raineer, rvevans:**
To summarize, and see if I understand you correctly: I should only end up with a total of 4 partitions then... 
2 GB for /swap, 
20 GB for /boot, 
70 GB for /home 
another 70 for / .

Is that right?

If this is the case, I have one more question:  how do I tell Ubuntu that my /home partition is the one it's supposed to use for /home?  Will it automagically recognize it in the file system, or is there somewhere I have to specify that?  What about the other partitiions?

---

### Post by pbaumgar on 2007-07-03
> **EvilMarshmallow said:**
> Thanks for some quick replies!

**alex_anthony:**
Not a bad suggestion... I'll definitely save my image once I get it done.  Even so, I'd like to separate the different functional areas, just in case the need arises one day...

**Raineer, rvevans:**
To summarize, and see if I understand you correctly: I should only end up with a total of 4 partitions then... 
2 GB for /swap, 
20 GB for /boot, 
70 GB for /home 
another 70 for / .

Is that right?

If this is the case, I have one more question:  how do I tell Ubuntu that my /home partition is the one it's supposed to use for /home?  Will it automagically recognize it in the file system, or is there somewhere I have to specify that?  What about the other partitiions?

Typically /swap should be about 1.5 times the amount of RAM you have.  20GB for a /boot partition is way too much.  The /boot partition is going to just hold the kernel image, so no need for it be more that 100-200MB at the most...

---

### Post by Raineer on 2007-07-03
Oops, that's my fault.. I was confusing /boot and /  (root).

---

### Post by EvilMarshmallow on 2007-07-03
OK, I have 2 GB RAM in this machine....

3 GB /swap
500 MB (just to be safe) /boot
78 GB  /root
78 GB /home

Any more suggestions?  How will the OS know that the /home partition is where I want my /home?

---

### Post by greg_g on 2007-07-03
If you have a separate home you don't need more than 10-15 for /.  My drive is 20 for /, 3 swap, and the rest (220ish) for /home.  And I only have a big / because I have more disk space than I need.


Oh, and when you install you will create those partitions and label them what you want them to be.  There will be a list to choose from.  There will be more than you recognize but just remember the 3 we talked about.  It should be fairly clear.  And by labeling them (/, /home, /swap) the system will know that the /home partition is where your home is.

EDIT: Correct me if I am wrong, but I think in the install they might say what "type" of partition it is, not "label."  But it will be one of the options when you create a partition.

---

### Post by jmz2 on 2007-07-06
I have read as well some people make partition for mounting /usr and /var on them.

My question is: why or what do you achieve doing partitions for:
/boot?
/var?
/usr?


I clearly see the utility for having a partition for /home but I would like to know why to make the others partitions. I have been looking for these answers but couldn't find anything.

As well, if I  installed 'all' Ubuntu in same partition, can I move /home to a new partition without reinstalling? I suppose I can, is it ok to do it without reinstalling or is it better if I reinstall?

Thanks.

---

### Post by twiceasworn on 2007-07-06
It really all just boils down to how you want your system organized.  Some people like having partitions separating /var, /usr etc.  I personally do it because I am used to it from the FreeBSD setups I have here at work.  I just like to keep things constant.

---

### Post by greg_g on 2007-07-06
> **jmz2 said:**
> I have read as well some people make partition for mounting /usr and /var on them.

My question is: why or what do you achieve doing partitions for:
/boot?
/var?
/usr?


I clearly see the utility for having a partition for /home but I would like to know why to make the others partitions. I have been looking for these answers but couldn't find anything.

As well, if I  installed 'all' Ubuntu in same partition, can I move /home to a new partition without reinstalling? I suppose I can, is it ok to do it without reinstalling or is it better if I reinstall?

Thanks.

Well, pretty much any Ubuntu Developer will tell you that those are not needed.  In fact, the reason why the default option for Ubuntu is only 1 partition for everything is because the things gained from separate partitions are few and tiny for the VAST majority of users.  However, having a separate /home partition is an advantage for some.

So, my two cents, if you want to partition more than the average user, just do / and /home.  Don't worry about the other ones, the advantages aren't there.

I hope I have helped,

EDIT: oh, and about moving your /home directory after an install.  I am sure there is a way, I just have not done it so I don't know, sorry.

greg

---

