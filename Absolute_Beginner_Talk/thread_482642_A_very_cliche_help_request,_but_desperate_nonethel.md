---
title: "A very cliche help request, but desperate nonetheless"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by deepsprings on 2007-06-23
Hi,

I know you will all despise me and deride me for this, and I deserve every bit of it.  However, I still need your help: I was very fascinated with the idea of linux, and I read much about it, but I was too ignorant, thinking I could trust myself with installing it on my system.

I was originally going to partially partition my laptop's harddrive, but decided later that I would run Linux from a completely different hard-drive.  So I took my 500gb harddrive with almost ALL of my data (so stupid! I wasn't even thinking) and selected that drive for use.  Then at the end of installation, I suddenly realized my error, checked my HD and alas, it said 430GB Free instead of the 50GB that were left on that.

I am almost dying, thinking about how stupid I acted.  But I am hoping for the best...

Is there anything I can do?  I am still awaiting an e-mail from my friend who is an expert  computer programmer, but probably barely acquainted with the data recovery process.

Should I take it in to Best Buy or some recovery place?  Keep in mind this is about 400GBs of harddrive space...

Thank you so much for your time
Paul

---

### Post by nutz on 2007-06-23
What did you lose? If you take it to a data recovery place it will not be cheap.

---

### Post by deepsprings on 2007-06-23
I have some of it backed up, but all of my files for my college's office, in addition to every paper I've ever written (although some of it is backed up online) for the last 3 years, and my music collection of 200gb, which is very dear to me (although definitely recoverable - I have them all on CD's - it'd just be a pain).  The pmost important things are the files for my college - I guess it would be cheaper to have them rescue a portion of the harddrive?

Is there any software I can use to help remedy the situation?  Any RELIABLE software?

---

### Post by fdrake on 2007-06-23
when u installed linux did u partition your hd or you formatted all you hard disk? if u dont know go to the terminal ( menu bar>application>accessories> terminal 
now type 
sudo aptitude install gparted
 
type the password for your username

after that type 
sudo gparted

on the application windows select your hard disk and tell us what do u see

---

### Post by BobCFC on 2007-06-23
See Private Message

---

### Post by fdrake on 2007-06-23
> **nutz said:**
> What did you lose? If you take it to a data recovery place it will not be cheap.

i don't think it will be possible recover a fully reformatted file system. only if u delete the data and don't overwrite all the disk.

---

### Post by Gen2ly on 2007-06-23
That's pretty valuable information, I'd take to to data recovery if you can at all afford it.  The up side of this is that Ubuntu isnt a huge installation like Windows, so possibly, maybe, the information on the later part of you hard drive is untouched.  Whatever you do it's best not to touch that drive until you find a way to recover that info.

---

### Post by deepsprings on 2007-06-23
okay, this is what it says:

partition: /dev/sdb1
filesystem: ext3
mountpoint: /media/disk
size: 462.89 GiB
used: 9.40 GiB
unused: 453.49 GiB

partition: /dev/sdb2
filesystem: extended
size: 2.86 GiB


partition: /dev/sdb5
filesystem: linux-swap
size: 2.86 GiB

---

### Post by jml on 2007-06-23
Much of your data may still be on the disk.  But the more you use your computer from this point on, the more likely you are to loose more data.  Reformating the hard drive during the install process erases the data in the Window's file allocation table, (FAT.)  It does not actually erase the files, simply the pointers to the files.  Your data is still at risk because your files are located on areas of the disc now marked as free.  Every time data is written to the disk, more of your data will be over-written.  Here is one resource I found via Google.  I have no personal experience with it, but it claims to do what you need.  If you do a google search on the term data recovery, you will also see listed at the top several sponsered links from companies that clain to be able to recover data from hard drives.  One caution, some of the prices seem unrealistically low.  From what I have read before, this type of data recovery can cost thousands of dollars and what they give back to you is the raw data.  You will still have a lot of work to do getting your files back into a usable form.

[http://www.z-a-recovery.com/index.html](http://www.z-a-recovery.com/index.html)

A free Linux option may be System Rescue CD.  I've included the link below.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Hope this will be of help.  Good Luck.

Joe

---

### Post by euler_fan on 2007-06-23
There are open source recovery tools you can use. Search the forums and you should find my old post asking a similar question (fortunately no need to actually go through the work, none of my files were worth it).

The first step is to make a disk image to another hard drive so that you can mess with it without destroying the files permanently. After that, use the tools on the image to do the analysis. Basically what they will do is try to recreate you file allocation tables.

There is a stickied thread over in servers and security forum and you might try reading that and posting there for additional assistance. It is more up their ally. Your problem is also related to computer forensics.

---

### Post by nutz on 2007-06-23
> **Dirk.R.Gently said:**
> That's pretty valuable information, I'd take to to data recovery if you can at all afford it.  The up side of this is that Ubuntu isnt a huge installation like Windows, so possibly, maybe, the information on the later part of you hard drive is untouched.  Whatever you do it's best not to touch that drive until you find a way to recover that info.


+1

As long as it hasn't been overwritten a good recovery specialist can recover it.

---

