---
title: "MacBook Air3,1: Restoring OS X"
date: 2012-02-23
forum: Apple Hardware Users
---

### Post by ryalho on 2012-02-23
Hello everyone!

I've been running 10.04 on my MacBook Air for about half a week or so. As I think about it more and more, I have decided that I would like to restore OS X to factory defaults but keep the Ubuntu partition. On top of that I would also like to add space to my Ubuntu partition and make the default system on the Mac, Ubuntu.

In other words, I want the free space created from restoring the Macintosh HD to factory defaults to be moved to the 20gig partition already allocated for Ubuntu.

This may get a bit messy so I am also willing to drop the OSX partition all together. Unfortunately, I am unsure whether Ubuntu alone will boot correctly as well as keep the laptop from blowing up in my face.

What is the best way to execute this?

Any help is good help for me!
Thanks!

---

### Post by Hellageddon on 2012-02-24
Well, first of all fire up your OS X and backup your data. 
I think we're talking about 10.7 here - that version needs approx. 10.6 GB on your HDD (fresh installed - no external applications etc.).

I don't know how much free disk space you will get, but I'd cut the free part of the Mac-OS partition and merge it afterwards with your Ubuntu-Partition.

---

### Post by ryalho on 2012-02-24
> **Hellageddon said:**
> Well, first of all fire up your OS X and backup your data. 
I think we're talking about 10.7 here - that version needs approx. 10.6 GB on your HDD (fresh installed - no external applications etc.).

I don't know how much free disk space you will get, but I'd cut the free part of the Mac-OS partition and merge it afterwards with your Ubuntu-Partition.

Hey thanks for replying! I want to keep at least 2 gigs on the mac partition just in case. 

So what you are saying is, I should just restore the mac partition? Restoring will only affect the 95gb partition correct? How do I merge this free space to Ubuntu without gparted? Just make these changes from the mac side?

Any further help would be much appreciated thanks!

---

### Post by ryalho on 2012-02-25
OK, so now I have a boatload of free space. Unfortunately I don't know how to merge this free space with Ubuntu.

---

### Post by soumya92 on 2012-02-27
You should try GParted. Make sure you backup your ubuntu install first, though, and allocate a lot of time for the merge operation. I've had it take a long time, but it works for what you need to do.

---

