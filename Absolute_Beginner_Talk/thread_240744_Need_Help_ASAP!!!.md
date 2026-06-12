---
title: "Need Help ASAP!!!"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by iampoch on 2006-08-21
I'm an absolute newbie.  Here's the scenario.  I finally decided to install Ubuntu in a previously unpartitioned 160GB HDD with Win XP.  I thought that I'd use Partition Magic first to create a partition for the Linux Setup (19GB in ext3 format the rest in NTFS). Ok so here's where I jerked off. I let Partition Magic install the new OS for me. Unfortunately, it created a partition (the 500.2MB swap file for Linux) in front of the the partition for Windows XP. Yup, I let it, because I honestly didn't know the implications. I was able to install Ubuntu, however, so I'm able to use the computer. Unfortunately, I can't boot Win XP even with the boot loader.

I tried fixing the problem by installing QTParted in Linux. I thought that by merging the 500MB partition to the partition using Win XP, I could solve the problem.  Unfortunately, when I tried to run QTParted, it says that there are no devices detected because I wasn't using a root account. I still need to dual-boot to Win XP so everyone please I need your help :( :( :(

---

### Post by encompass on 2006-08-21
We don't help windows users!  Just kidding... :D ;) :D 
Check the settings in your bios... make sure you have something called LBA support turned on... I had a similar issue.  I was installing Fedora core for a class of students and in front of everyone I lost someones windows boot.  That was bad.  So I searched the net... and if I remember... it was something to do with lba support or something like that.  It lets things boot past the MBA or something to that effect.
If you still don't get it... tell me and I can start looking again.

---

### Post by iampoch on 2006-08-21
Hehe :D Actually, I'm starting to love Ubuntu a whole lot more :D but I still need some of the programs in Windows, though, so I can't go into a complete transition :) Ok, I'll try what you told me. I also downloaded a partition manager ISO just in case, I'm keeping my fingers crossed all the way :)

This is a great community we have here :) thanks :)

---

### Post by Sef on 2006-08-21
> I thought that I'd use Partition Magic first to create a partition for the Linux Setup

For your information:  Partition Magic does not go well with Linux.  Best to use another partitioner.  Glad it did not give you a problem, but often it has.

---

### Post by raggit on 2006-08-21
If you still need/want to use windows programs look into a project called Crossover for linux.  I"m a complete newb like yourself and I installed Crossover just this morning and within 5 minutes was running Internet Explorer on my linux box.  Other windows programs can be installed as well.

You can find the crossover project here
[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

[i]<removed>
It's not allowed tp promote piracy and the like on these boards.
-- Artificial Intelligence[/i]

---

### Post by encompass on 2006-08-21
> This is a great community we have here  thanks
Reply With Quote
So is your problem fixed? did you get your windows partition to boot?

---

### Post by iampoch on 2006-08-22
Hi, sorry for the late reply :( I tried the LBA thingy but I can't seem to find it :( Next stop was a partition manager live CD. I waited for 20 hrs to do its thing, that's why I wasn't able to reply.  I tried to delete the 500MB partition in first place and then tried to move the 120GB partition of WinXP, which should've taken 20+ hours.  but it didn't do a thing :( I'm up my knees in tears right now :(

@Sef - I eventually didn't use Partition Magic to install the OS, but it still created that darn partition in front of the WinXP partition.  

I'm still unable to boot and I honestly don't want to reformat my hard drive just yet :(  Please help me :(

---

### Post by bdalzell on 2006-08-22
This is an answer only to part of your problem. You mentioned you tried qtparted and it wanted you to be root to run it.

In Ubuntu there is no root user as such. You access commands that root needs to run by proceeding them with sudo as in:

sudo qtparted

and then when it asks for password - the password is you user password.

Gparted is also useful. If you boot from a Ubuntu live disk you can actually mount all your file systems(partitions) and look to see if the data is unharmed. Gparted will tell you the device name of the partitions.

In my experience as a relative beginner with Linux learning how it handles partitions and how to mount and unmount them has been the most useful thing I have had to learn. 

There is a great newbie Ubuntu HOWTO thread at:

[http://www.ubuntuforums.org/showthread.php?t=13042](http://www.ubuntuforums.org/showthread.php?t=13042)

---

### Post by bdalzell on 2006-08-22
This is an answer only to part of your problem. You mentioned you tried qtparted and it wanted you to be root to run it.

In Ubuntu there is no root user as such. You access commands that root needs to run by proceeding them with sudo as in:

sudo qtparted

and then when it asks for password - the password is you user password.

Gparted is also useful. If you boot from a Ubuntu live disk you can actually mount all your file systems(partitions) and look to see if the data is unharmed. Gparted will tell you the device name of the partitions.

In my experience as a relative beginner with Linux learning how it handles partitions and how to mount and unmount them has been the most useful thing I have had to learn. 

There is a great newbie Ubuntu HOWTO thread at:

[http://www.ubuntuforums.org/showthread.php?t=13042](http://www.ubuntuforums.org/showthread.php?t=13042)

---

### Post by iampoch on 2006-08-23
hehe, thanks for all your help :) I managed to do something in my Ubuntu as well, so it was a reformat for me, but bdalzell you're right. I have to leart about partitions, particularly in the way Linux handles it :) I'll also be extra careful with using partition managers, Partition Magic in particular :)

---

### Post by iampoch on 2006-08-23
Update: I just found out that the booboo I did with Ubuntu earlier was actually the buggy xserver update :( oh well, at least I got to clean install :(

---

