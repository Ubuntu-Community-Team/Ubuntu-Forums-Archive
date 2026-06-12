---
title: "Booting prolems:NEED URGENT HELP"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-01-30
Hi everyone,
I have recently been doing a lot of change to my desktop and this is what i have done:
1) deleted windows vista partition
2) installed ubuntu-server on one of the partition

However, when I reboot my machine, my desktop says that it can't mount my ubuntu server partition.

My question is:
1) How do I delete the MBR and perform a clean installation with my ubuntu cd?
2) How do i do this using "manual" as my partition option? (PS I do not want to use guided because I have a lot of partitions and I actually want to specify the space for each partition)
3) Do i need to allocate a new partition just for the MBR? (at 0?)
4) Aside from ext3 and swap, what other patition do I need?

Right now I am using my windows cd to completely format my ubuntu and windows partition.

PLEASE HELP ME!!!

and this question is rather irrelevant: How much more useful is the ubuntu server? Could i install all its features with ubuntu client 7.10?

---

### Post by JoshuaRL on 2008-01-30
1) If you deleted Vista then that should have deleted MBR.  What makes you sure MBR is still there?
2) Yes, you would want to do that with manual.  Guided lets you use a slider to decide how big the partition will be.  But if you already have your driver partitioned how you like and you need to install to a particular partition, then use the manual option.  Breath deeply and read everything carefully.  You'll be fine.
3) If you don't have Windows, you don't need MBR.
4) For Ubuntu, none.  The filesystem will reside on ext3 and the swap will be swap.


Yes you could run all the features from regular Ubuntu.  The difference is that it's faster to run a headless (GUI free) system in a server setting, and the install CD for server comes with a choice to install the LAMP stack.  But you can get that stack other ways.

---

### Post by oedha on 2008-01-30
1. to delete the MBR ..... from windows installation cd....go to recovery mode
or type fixmbr

2.yes...its better for you to choose "manual" partition and from here...
3. no, actually if you have deleted it....why dont you put ubuntu on it
4. ext needed....swap will be needed if your RAM under 1GB

ubuntu server : will be used if you plan to make a server
i suggest you to find ubuntu 7.10 live CD.......

regards;
~E~

---

### Post by disappearedng on 2008-01-30
Hm.. the funny thing is how do i ensure that grub is at space 0 in the harddrive partition?

so do i just delete all the partition and allocate 
1st) the 30GB that I want for Ubuntu server 
2nd) swap space

Note: it says that the free space starts from  (0,1,0) and ends at ....
is this the correct address for the ubuntu partition ext3?

is there a difference?

---

### Post by JoshuaRL on 2008-01-30
> **oedha said:**
> swap will be needed if your RAM under 1GB

Actually, you can run into some instabilities even if you have more than 1gb RAM.  The way Linux works is that instead of having a "page file" like in Windows, it has a dedicated partition for RAM overrun.  So if you don't have a swap partition at the time where you're using the most RAM, your system can become unstable.  Kind of like tires that are only bad at highway speeds, you don't really want to mess with that.  Much better to have a swap partition.

---

### Post by disappearedng on 2008-01-30
So I installed the Ubuntu server after deleting the previous ubuntu and windows partition...

When installation was completed, I get 
"GRUB loading stage 1.5
GRUB loading. please wait ...
Error 17"

What is going on?

---

### Post by oedha on 2008-01-30
error 17.....can you check [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

to joushuarl....thanks to remainding me....:) 

~E~

---

### Post by JoshuaRL on 2008-01-30
No problem dude.  :guitar:

And Grub Error 17 just means that Grub can't find grub.list.  If you still have problems after following those directions, try burning off a Super Grub CD.  It's a live CD and will help fix any problems with Grub.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

(Now that I mention it, I should probably burn myself off a copy in case I ever have problems.)

---

