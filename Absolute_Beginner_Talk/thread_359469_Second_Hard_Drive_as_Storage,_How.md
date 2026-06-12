---
title: "Second Hard Drive as Storage, How?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Dragon43 on 2007-02-12
On my windows machine I use a second hard drive either as additional storage or as a 'mirrored' HD.  I have a little Western Digital utility on a floppy that will mirror a drive completely if one of the drives is a Western Digital. It is for installing a new drive.   I use 'mobile trays' and use old hard drives as back-ups, once a week or so.  I copy and then unplug them and I have a total back-up in case of disaster.  Cheap and easy as older 5400RPM  HD's are cheap to come by and I do not have over 14 Gig's on any HD in any of my machines. Mostly Win-98se machines, I do not like XP.

So I want to do the same with my 'Ubuntu' machine.  How do I get 6.06 to see and use a second hard drive?  Will the Western Digital utility work with Ubuntu?  If I try to use it, can it crash or mess up my 6.06?  I am new and I do not want to lose the ground I have made by doing something stupid until I have myself a back up of where I am now.

Tell me or point me in the right direction please.  Use small words, I'm not that swift with computers.

---

### Post by aysiu on 2007-02-12
One of these may help.

For FAT32 or NTFS:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For Ext3:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by kidders on 2007-02-12
Hi there,

> **Dragon43 said:**
> How do I get 6.06 to see and use a second hard drive?Ubuntu automatically detects hardware changes, so you don't have to do anything, really. To make use of the new drive, partition/format it and mount it somewhere convenient.

> **Dragon43 said:**
> Will the Western Digital utility work with Ubuntu?You don't need any special utilities to clone disk drives with Linux. The **cp** or **dd** commands tend to suit most peoples' purposes, really.

---

### Post by Dragon43 on 2007-02-12
I should add that I have no dual boot.  My Ubuntu machine is all that is on it.  Same for the others on the in-house network.  All are single OS machines.  I will run 6 - 40 GIG hard drives on the Ubuntu machine for many years unless I win a lottery.

Thje biggest HD I have is a Seagate 120 and a WD- 80 on other machines.

Will Ubuntu run a 10,000RPM HD?

---

### Post by Dragon43 on 2007-02-12
Wow, replys already.  Explain the **CP** and **DD** of which you speak please.

I tried top use 2 hard drives and it did not even boot.????

Admittdly that was back before I got it workig as good as it is now.  I can try again.

Thanks in advance.

Gus aka Dragon43

---

### Post by Dragon43 on 2007-02-12
**"aysiu"**
Already read those links and they did not seem to be the correct thing I am looking for.  Did I miss read?

---

### Post by kidders on 2007-02-12
> **Dragon43 said:**
> Will Ubuntu run a 10,000RPM HD?The speed your disks rotate at makes little or no difference to your OS, afaik. You'll be fine. :-)

> **Dragon43 said:**
> Explain the **CP** and **DD** of which you speak please.**cp** copies files and **dd** dumps bytecode from one place to another. (Everything you could want to know about either is in their man pages.)

---

### Post by aysiu on 2007-02-12
> **Dragon43 said:**
> **"aysiu"**
Already read those links and they did not seem to be the correct thing I am looking for.  Did I miss read?
I may have misread, actually.

Is the situation that you have a hard drive you want to see in Ubuntu? I thought that's what your question was, but I was a bit confused by some of the technical terms in your original post.

---

### Post by Dragon43 on 2007-02-12
Thanks folks, reading up on Commands now.

Lots to learn.

Gus

---

