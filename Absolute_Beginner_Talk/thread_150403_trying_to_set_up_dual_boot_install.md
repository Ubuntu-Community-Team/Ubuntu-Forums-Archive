---
title: "trying to set up dual boot install"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by ScottyI on 2006-03-26
I have windows XP (ntfs) installed on an existing partition (basically 80.0 GB out of an 80.1 GB drive), leaving no room for ubuntu.

I'd like to use around 20GB of the 30GB of remaining free space for the install. How do I do this? 

I started the install but I got nervous once I got to the menus regarding partitioning, etc. I'd like to not blow away windoze...

---

### Post by jimrz on 2006-03-26
Welcome,

   Take look [[COLOR="Sienna"]**_here_**[/COLOR]]("http://users.bigpond.net.au/hermanzone/") for an excellent guide to setting up your ubuntu / xp dual boot, including how to re-size your win partion during the process to accomodate ubuntu.

---

### Post by RRS on 2006-03-26
First defragment the drive and then backup any data you can't afford to lose, the risk is slight but there is one.

Then read and follow the instructions on [this site]("http://users.bigpond.net.au/hermanzone/index.htm").

Of the installation options the author covers I'd recommend setting up a fat32 partition for sharing data with windows.

10gb is more then adequate for Ubunto.

After defragging windows you can check the actual amount of disc space you're using and simply round up from that number to allow for some expansion room.

Partition the remaining space for fat32. 

You will also be asked to allow the creation of a swap partition, let it. This will be sized according to the amount of ram you have and I believe it's taken from the ext3(Ubuntu) partition, no problem.

I'm currently running dual boot on 2 machines, one with 40g and the other an 80g like yours. My partition sizes are 10/10/20 and 20/20/40 with the largest on each being the fat32.

Welcome aboard :)

Edit: gotta learn to type faster

---

### Post by jason.b.c on 2006-03-26
Well first start off by cleaning and defragmenting your hard drive..

Start menu>system tools>disk cleanup      then  disk defragmenter.

Then if you've got a program in your computer like powerquest partition magic or something, you would use the option called RESIZE partition.

Just make sure you have defragmented the hard drive though!

Just resize your drive and put in the ubuntu cd, then restart and you should be able to install to the new partition you just made ,  just make sure you format the new partition as fat 32.

---

### Post by ScottyI on 2006-03-26
Ill be checking out the links and trying it out today. :mrgreen:

---

