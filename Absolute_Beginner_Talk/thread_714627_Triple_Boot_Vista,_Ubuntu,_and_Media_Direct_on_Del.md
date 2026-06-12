---
title: "Triple Boot Vista, Ubuntu, and Media Direct on Dell"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Baylor Bear Matt on 2008-03-04
Hi yall.  This is my first post on the Ubuntu Forums.  I hope yall are able to help answer my (unfortunately) numerous questions!

First off, I have tried to learn about Linux before by dual booting XP and Ubuntu 6.10 on my desktop computer.  That was a great experience for me.  However,  that was right before I left for college, and so I wasn't able to learn much before I left with my new laptop.

Well, its been over a semester now, and I can't ignore the call of freedom from vista anymore.  Unfortunately, I don't know enough about linux to completely get rid of windows just yet.  So, I would like to dual boot vista and ubuntu 7.10 on my laptop.  I have a Dell Inspiron E1705 with 2GB RAM, 100 GB 7200 RPM HDD, et cetera. 

However, in researching dual booting on a dell laptop, I've found that Dell's Media Direct button (which enables quick access to your media files) functions as its own OS on the disk, and that it takes some know how to get windows and linux to play nicely on the laptop and maintain the functionality of this button (which I personally don't use, but might in the future).

The two best solutions I've found to get everything working on my laptop are the following:
[http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)
[http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html](http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html)

However, they do not agree on how to partition the hard drive.  One recommends having a shared ext3 partition space for both OSs, while the other doesn't talk about a shared partition at all.  In addition, the one that does talk about a shared partition, a comment on the bottom says that a shared NTSF partition would be a better idea.

This wouldn't be a big deal at all, except for that, since I've had the laptop a while now, I have quite a few important programs and files that I need to keep.  I need to transfer my files temporarily to an external, and be able to bring them back onto my computer after I'm done setting everything up. So, I don't exactly know what to do in order to preserve my files.  This brings me to my questions.

I should also mention that I would like to use an external hard drive to hold files for both OSs to use, so I do not know if a shared partition would be important for me.

1. If I just copy my hard drive onto an external, and then follow the instructions of the one recommending a shared partition, would I be able to pull all of my files back onto the shared partition?
Specifically, since the files and programs were on my windows partition originally, would it be possible to then put them onto the ext3 partition and them work fine?

2.  Would a shared NTSF or ext3 partition work better?  (I read a shared ext3 partition does not include journaling.)

3.  Or, should I just forget about the shared partition and bring all of my displaced files back into a windows partition?  I think this would eliminate possible compatibility issues for the files on a shared partition (I'm not sure if compatibility errors exist, though).

4.  With an external to share files between the OSs, should I bother with a shared partition?  What should I format the external hard drive to for best sharing between the two OSs?

I realize these are a lot of questions, and I am sorry i'm a little long winded.  I'm just trying to avoid having to clarify myself.  Any, and I mean any, help would be greatly appreciated!  Thanks in advance!

---

### Post by talsemgeest on 2008-03-04
Hi, and I'm glad to help out a person intelligent enough to switch to ubuntu.

First of all, I think that if you have an external hd, then there isn't much use in making a shared partition.

As of ubuntu 7.10, ubuntu comes with built in NTFS read and write support, so you can still access all of your files that are on the vista partition.

My suggestion to you would be that you let the ubuntu installer figure it out. When it comes to the partitioning, simply move the slider on the "resize" to whatever you want it to be, and then continue with the installation.

I hope this helps, and good on you for changing to ubuntu!

---

