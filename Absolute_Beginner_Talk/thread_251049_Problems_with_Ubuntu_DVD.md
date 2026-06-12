---
title: "Problems with Ubuntu DVD"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2006-09-04
I downloaded the Ubuntu DVD for 64 bit systems I burned the iso as an image using nero, I boot with the DVD and click on start or install ubuntu. It starts installing but then it stops on the line that ends with **io scheduler cfq registered**.

Can anyone tell me what´s wrong with my system or what it is that I´m not doing right?

Thanks in advance!

---

### Post by dunklegend on 2006-09-04
I was able to get pass the error by setting the parameter noapic in the boot line.:) 
Now I´m in the **Prepare mount points** screen, and I don´t know what to do here :confused:

---

### Post by dunklegend on 2006-09-04
I have a 320 GB hdd and it only has a 75 GB partition for windows XP the rest of the hard drive is unallocated space.
Can someone tell me how to setup the partitions?
I would like to make a 50 GB partition for Ubuntu and leave the rest formatted as FAT32 so windows and linux can write to it.

Any help will be appreciated.
Thanks in advance!

PS: If someone can help me in msn messenger that would be great :)

---

### Post by dunklegend on 2006-09-05
Can someone help me in MSN messenger when I make the partitions and start installing the installer crashes.

---

### Post by dunklegend on 2006-09-05
In which forum should I post the error message that I get when the installer crashes? So far I haven't got any answers in this forum the only answers I got were from TG Forumz that is a hardware forum.

Maybe nobody that knows linux reads this forum.

---

### Post by CaveRat on 2006-09-05
> **dunklegend said:**
> In which forum should I post the error message that I get when the installer crashes? So far I haven't got any answers in this forum the only answers I got were from TG Forumz that is a hardware forum.

Maybe nobody that knows linux reads this forum.

Are you still there? I had a problem trying to figure out a good partition table myself. It took six tries, but I found one that worked for me.

---

### Post by user1397 on 2006-09-05
> **dunklegend said:**
> In which forum should I post the error message that I get when the installer crashes? So far I haven't got any answers in this forum the only answers I got were from TG Forumz that is a hardware forum.

Maybe nobody that knows linux reads this forum.yep, this is the right place to ask for beginners, hence the 'absolute beginner talk' name :p

anyway, to help you out with your problem, you got to give us some specifics.
How much ram do you have?  what kind of processor do you have?  is it 32-bit (intel and amd athlon/sempron) or 64-bit(amd64/intel xeon)?

also, here's a good page depicting the various partitioning schemes: [http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by dunklegend on 2006-09-05
Yes I'm here.
What worked for you?
I was wondering how much space to leave for a /home directory.
I'll leave 50GB for Ubuntu and 4GB for swap (because it said that it had to be about double of the RAM you have and my machine has 2 GB). The rest I'll leave it as a FAT32 partition to share it with windows.

---

### Post by dunklegend on 2006-09-05
> **erik1397 said:**
> yep, this is the right place to ask for beginners, hence the 'absolute beginner talk' name :p

anyway, to help you out with your problem, you got to give us some specifics.
How much ram do you have?  what kind of processor do you have?  is it 32-bit (intel and amd athlon/sempron) or 64-bit(amd64/intel xeon)?

Mobo: Epox MF570 SLI
CPU: AMD Athlon 64 X2 3800+
RAM: Geil 2GB(2X1 GB) DDR2 800
GPU: GeForce 6600 256MB Video Card. 

I leave work in just a little while but I'll reply as soon as I get home.

---

### Post by user1397 on 2006-09-05
> **dunklegend said:**
> Yes I'm here.
What worked for you?
I was wondering how much space to leave for a /home directory.
I'll leave 50GB for Ubuntu and 4GB for swap (because it said that it had to be about double of the RAM you have and my machine has 2 GB). The rest I'll leave it as a FAT32 partition to share it with windows.ah, so you have 2GB of ram.  then you don't need 4GB swap.  a large swap area is only useful for machines with inadequate memory.  since you have a lot, you can make a 128MB swap area, and it'll probably never be used. so dont waste space on swap.  as for the partitioning scheme, i suggest you use this one:  [IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG]

that's just sort of a guideline.  try to divide your 320 Gig HD into portions about that size.  use the gparted program (called Gnome Partitioner, it's in system > administration) that is included in your live cd to make all partitions, and then try to install it.

---

### Post by CaveRat on 2006-09-05
> **erik1397 said:**
> ah, so you have 2GB of ram.  then you don't need 4GB swap.  a large swap area is only useful for machines with inadequate memory.  since you have a lot, you can make a 128MB swap area, and it'll probably never be used. so dont waste space on swap.  as for the partitioning scheme, i suggest you use this one:  [IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG]

I have a question for you myself. I just checked my partitions a short while ago and noticed what looks like a full 3 gig swap. I am running with 768mb of ram at the moment. Is there any way to access swap to see what's going on?

---

### Post by dunklegend on 2006-09-05
> **CaveRat said:**
> I have a question for you myself. I just checked my partitions a short while ago and noticed what looks like a full 3 gig swap. I am running with 768mb of ram at the moment. Is there any way to access swap to see what's going on?

I don't know but I'll try to find out and if I do I'll let you know. :)

---

### Post by dunklegend on 2006-09-05
> **erik1397 said:**
> ah, so you have 2GB of ram.  then you don't need 4GB swap.  a large swap area is only useful for machines with inadequate memory.  since you have a lot, you can make a 128MB swap area, and it'll probably never be used. so dont waste space on swap.  as for the partitioning scheme, i suggest you use this one:  [IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG]

that's just sort of a guideline.  try to divide your 300 Gig HD into portions about that size.  use the gparted program (called Gnome Partitioner, it's in system > administration) that is included in your live cd to make all partitions, and then try to install it.

Do you suggest to make the partitions before trying to install it.
I was trying to make the partitions with the partition program that the installer brings up but the installer was crashing on me so I might be doing something wrong.

How can I use the gparted program do I just boot from the live cd look for it in system>administration and do it from there?

---

### Post by CaveRat on 2006-09-05
> **dunklegend said:**
> I don't know but I'll try to find out and if I do I'll let you know. :)

Oh thanks. I was hoping Eric1397 was still observing this thread. Looks like he's been around a good while and knows what's what by all his how to's listed.

---

### Post by user1397 on 2006-09-05
> **CaveRat said:**
> I have a question for you myself. I just checked my partitions a short while ago and noticed what looks like a full 3 gig swap. I am running with 768mb of ram at the moment. Is there any way to access swap to see what's going on?yes, there's a command for that.  in a terminal (applications > accessories > terminal) type: ```
free -m
``` NOTE: the command 'free' without the '-m' would give the results in kilobytes, while the '-m' gives the results in...yep, you guessed it, megabytes.

---

### Post by CaveRat on 2006-09-05
> **dunklegend said:**
> Do you suggest to make the partitions before trying to install it.
I was trying to make the partitions with the partition program that the installer brings up but the installer was crashing on me so I might be doing something wrong.

How can I use the gparted program do I just boot from the live cd look for it in system>administration and do it from there?

That's what I did. Then when I started the install, I confirmed what I wanted it to do in the partition manager window.

---

### Post by user1397 on 2006-09-05
[quote=dunklegend]Do you suggest to make the partitions before trying to install it.[/quote]I do suggest making the partitions before the clicking on the installer, the installer can be buggy sometimes.  REMEMBER: back up all important data on your windows partition so that you don't smash your head into the monitor after you lose 50 Gigs of music, photos, and movies!!!
[quote=dunklegend]How can I use the gparted program do I just boot from the live cd look for it in system>administration and do it from there?[/quote]yep, exactly

---

### Post by dunklegend on 2006-09-05
Thanks

---

### Post by user1397 on 2006-09-05
also, your ubuntu dvd might be corrupt if it doesn't work at all.  where did you download it from?  i downloaded the ubuntu PC dvd from [here]("http://ie.releases.ubuntu.com/ubuntu-cdimage/releases/6.06/release/"), and it worked fine for me.

When you burn the dvd, you might want to set the burning speed at 4x to ensure no corruption takes place.  if your program doesn't offer that, try this free windows burning app: [http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

and here's a great guide on how to download and burn an ubuntu cd correctly:[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by CaveRat on 2006-09-05
> **erik1397 said:**
> yes, there's a command for that.  in a terminal (applications > accessories > terminal) type: ```
free -m
``` NOTE: the command 'free' without the '-m' would give the results in kilobytes, while the '-m' gives the results in...yep, you guessed it, megabytes.

Hey thanks for that. Odd though. When I looked at the swap partition in system/disks/partitions, the blue bar was all the way across. I just did your how to and it says 0 swap of 3074 is used.

---

### Post by user1397 on 2006-09-05
> **CaveRat said:**
> Hey thanks for that. Odd though. When I looked at the swap partition in system/disks/partitions, the blue bar was all the way across. I just did your how to and it says 0 swap of 3074 is used.in system > disks > partitions, the bar literally means how much space that partition takes up, *not* how much memory is being used.  but as the **free -m **command has shown you, none of the 3GB of swap is being used, and so is a waste of space.  (that is, if you really need the space.  if you have a large hard drive, and a lot of memory, you barely need any swap, but if you have a low amount of memory and a small HD, you should consider a large swap area.)

you can change the swap partition, and make it smaller if you want to, using the gparted program like I mentioned earlier.  WARNING: don't do this while in your installed ubuntu, only do it from the live cd, or else your kernel might get messed up.

---

### Post by dunklegend on 2006-09-05
I started installing in text mode and it hangs on a window that says installing the base system. the bar is at 45% and on the bottom it says configuring makedev.

Am I doing something wrong? Is there a command that I need to put in the line? The only one I added is noapic that is the only way my computer boots the DVD.

---

### Post by dunklegend on 2006-09-05
By the way it´s been stuck in 45% for about 10-15 minutes.
Is it safe to say that it´s not going to finish the installation?
Is there a way to cancel the installation?

---

### Post by dunklegend on 2006-09-05
I finally installed my dual boot. :) 
Now I´m going to try it on another Hard Drive to see if I learned anything. :KS

---

