---
title: "how much room does ubuntu need?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by crapshoot on 2006-12-06
how much room do i need to install ubuntu?  i have about 5 megs spare to partition.

---

### Post by mattmole on 2006-12-06
Hiya,

I presume you mean 5gigs. Erm.

How much RAM has your system got? Ive heard people say that if you have about 2gigs of RAM swap is not necessary.

I personally have a 10GB partition for ubuntu and a 1gb partition for swap, I have approx 760mb RAM.

Out network admin at work uses about 7.5GB for the partition storing ubuntu.

Hope that helps. Matt

---

### Post by crapshoot on 2006-12-06
yes, 5gigs.  where so i find the RAM? and what is swap?

---

### Post by mattmole on 2006-12-06
If you are using windows, right click on my computer on the desktop and on the first screen that shows up you should see the RAM of your system.

I think there was another post in the forum which was good for partitioning etc. Ill have a look.

Matt

---

### Post by crapshoot on 2006-12-06
it says 261,424 KB.  i guess that rounds out to 256 ;o

but, what is "swap" that you mentioned in your reply?

---

### Post by bodhi.zazen on 2006-12-06
I think the lowest you can go is 3.5 Gb

I would make swap 512 Mb

---

### Post by mattmole on 2006-12-06
As far as Im aware SWAP is used to extend your RAM. So for very memory intensive things the swap partition will be used partially as RAM.

This is my VERY VERY VERY basic knowledge, and could be incorrect!

I would agree I think 512mb swap and about a 4.5Gb "ubuntu" partition. From now on I will call the ubuntu partition "/"

The below link is a good guide to general ubuntu things.
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Hope that helps.

Matt

---

### Post by crapshoot on 2006-12-06
what is "swap"?

---

### Post by CatKiller on 2006-12-06
> **crapshoot said:**
> what is "swap"?

[http://en.wikipedia.org/wiki/Swap_memory#Swapping_in_the_Linux_and_BSD_operating_systems](http://en.wikipedia.org/wiki/Swap_memory#Swapping_in_the_Linux_and_BSD_operating_systems)

---

### Post by mattmole on 2006-12-06
Thanks for that CatKiller! I now know a bit more about swap :)

Matt

---

### Post by S1NGH on 2006-12-06
> **crapshoot said:**
> yes, 5gigs.  where so i find the RAM? and what is swap?

 i assume you are running windows now, in-order to find out the amount of RAM your system has, right-click "My Computer" click on "Properties" and finally click on the "General Tab". You will be presented most of the information on system hardware that you currently have, i.e. RAM, Processor speed etc...

Swap memory is just like virtual memory the one you use or see in windows...this block of memory, is actually space on the hard drive.  The operating system reserves a space on the hard drive for &#8220;swap space&#8221;. The operating system can use this virtual memory (or swap space), if it runs out of physical memory.  This is the reason it is called &#8220;swap&#8221; memory, the operating system takes some data that it doesn't think you will want for a while, and saves that to disk in this reserved space.

edit: sorry for the late reply, i had to rush somewhere and took me half-an-hour and left the reply incomplete, and just arrived now and completed it.
hope you got everything you wanted help with, if you get any problems, eg. in the installation process, just ask ;) we will be glad to help you out, not only you, anyone else!

---

### Post by crapshoot on 2006-12-06
thank you all for the answers.  it looks like 5GB won't really cut it, but i may be reading it all wrong.  then i would have to figure out how to partition out space.  

i assume that you need other software to do all this?

---

### Post by bodhi.zazen on 2006-12-06
> **crapshoot said:**
> thank you all for the answers.  it looks like 5GB won't really cut it, but i may be reading it all wrong.  then i would have to figure out how to partition out space.  

i assume that you need other software to do all this?

LOL :lol:

gparted will resize you partitions for you.

First defragment you HD from windows.

Then boot the desktop CD

In a terminal type:```
sudo gparted
```

[Gparted how to resize](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by mattmole on 2006-12-06
Id say it can be even easier than that. You could always boot up the desktop CD. Then just click the INSTALL icon on the desktop and as part of the install procedure it will let you do the partitioning.

I agree, defragment through windows first!

---

### Post by crapshoot on 2006-12-06
does this also work on win2K?

i just ordered the free cd but i want to get the groundwork set up before it gets here.

---

### Post by bodhi.zazen on 2006-12-06
> **crapshoot said:**
> does this also work on win2K?

i just ordered the free cd but i want to get the groundwork set up before it gets here.

Yes, but how are you going to partition ?

You can always download and burn the [Gparted Live CD](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by S1NGH on 2006-12-06
> **bodhi.zazen said:**
> Yes, but how are you going to partition ?

You can always download and burn the [Gparted Live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")

 or you could wait for the disc to arrrive... about the partitioning, since you have 5GB left for spare use, and would recommend to have atleast

2-3 GB of root space;
if 3 GB(3072 MB) for (/) root space has been taken - as ext3 (but it's up to you);
have hmm... 1535 MB for /home (i always use reiserfs file system); 
and the rest for SWAP - 513 MB, as some bytes of space are used up initially.

hope this helps.

---

### Post by ajgreeny on 2006-12-06
I wouls suggest you leave as much space as possible for ubuntu, and reduce you windows partition as far as you feel makes practical sense.  If you are like me you will quickly find that you use ubuntu all the time and only occasionally boot into windows for some specific purpose (in my case, an old scanner not recognised by linux, and a great serif DTP prog which knocks spots off scribus [unfortunately]).  I tend to boot into windows just to update it once a month, and as I don't play games, almost everything else is ubuntu all the way.

The first time I installed ubuntu (v5.04), after playing around with other distros, I left myself with nowhere near enough room, so had to backup my home files and reinstall onto a bigger partition, thereby reducing windows even further.  If you really don't have much space, think about getting another hard disk, they are pretty cheap these days and easy to fit yourself.  Put ubuntu on that and you should have a good system.

---

