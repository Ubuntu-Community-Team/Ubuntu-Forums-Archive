---
title: "Problem with partitioning hard disk"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by L.G.S on 2007-08-27
Well I had a look around but cannot find an answer.

I have got to the stage in the installing (using alternate CD) process where it needs to create a partition.

I chose option one for the computer to do it automatic, but I want to dual boot Ubuntu with XP as well. I have read the dual boot guide, but this is my problem:

My HDD is 80GB. I have 24GB free. When it asks me how much space I want to use for the partition, it says I can have a minimum of 51GB and a maximum of 73GB. If I enter anything less than 63GB, it says not big enough and won't let me continue. I tried to enter 63GB and it started but then gave me an error (which at the time I did not write down, so I do not remember it). 

So is there any way to make my partition say 15GB in size? I really want to use Ubuntu.

I have a NTFS HDD.

---

### Post by Happy_Man on 2007-08-27
Right.... choose a number between those two. The numbers are showing how big it will make XP, not how big it will make Ubuntu.

---

### Post by carverj on 2007-08-27
You must choose the free space partition (the 24GB free part) and make it root (which is represented by a / symbol) and then allocate some swap space at the end of the drive (1.5 times the amount of RAM from memory).
Good luck and never give up!! It's worth it!!

---

### Post by L.G.S on 2007-08-27
This is where I'm confused. I'm a noob at all this so everything is alien.

Sorry if its annoying, but can somebody take me step through step? I feel if I do it myself I'm going to completely ruin my HD and lose files.

---

### Post by Happy_Man on 2007-08-27
> **L.G.S said:**
> This is where I'm confused. I'm a noob at all this so everything is alien.

Sorry if its annoying, but can somebody take me step through step? I feel if I do it myself I'm going to completely ruin my HD and lose files.
If you're scared, just choose the auto-resizer. It knows exactly what it's doing.

---

### Post by L.G.S on 2007-08-27
I'm not scared, just unsure.

This is where I get stuck, it comes up after I choose the auto partition choice and with a red background says "For some reason it is impossible to resize your partition". 

I did a dskchk and everything went okay,  but it still says it??

---

### Post by Magneticgravity on 2007-08-27
Use the guided option, where Ubuntu uses the remaining available memory and does it all for you.

---

### Post by L.G.S on 2007-08-27
In the setup you have:

>  Guided - resize SCSI1 (0,0,0), partition #1 (hda1) and use freed s
 Guided - use entire disk
 Guided - use entire disk and set up LVM
 Manual                                

I assume you are talking about option one, but as I mentioned I get the error I posted.

I can't use option 2, because I want to dual boot. Nor option 3. The last option I have been trying, but it has been so confusing even with the graphical walkthrough.

---

### Post by Happy_Man on 2007-08-27
Right, I hate Feisty's version of the installer. The previous versions did it better. First off, choose Manual. Then, right-click the NTFS partition, and choose edit. 

Drag the bar down, knowing that the yetllow indicates the amount of space used. (Defragment your drive in Windows at least three times before doing this.) 

Then, select the unallocated space and make one 5 GB partition in ext3 format, one 512 MB partition in swap format, and give the rest over to another partition in ext3 format. 

Hit apply. 

When the next screen comes up, mount the 5 GB partition as /, the other ext3 partition as /home, and the swap partition as swap. And from there, it's easy!

---

### Post by L.G.S on 2007-08-29
Thanks for the help. Now I have more problems... When I open certain programs (its generally random) the program just opens up the box and doesn't load. Once it has done that it won't work again until I restart 2 and sometimes 3 times. It's happened for most programs so far.

---

