---
title: "Partition questions"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Trurl on 2006-06-13
Hi everyone,

   Everything is currently running fine in Dapper except that somehow, my 3 GB root partition is full. I am not sure how this happened since I didn't think I had installed anything in that partition. Perhaps I don't understand how installing works in linux. I have a 9 GB free on my /home partition so I didn't think I had a disk problem. Any ideas? 

Thanks,

Trurl

---

### Post by johnc4510 on 2006-06-13
Linux installs the base system on the / or root partition. The /home partition is for all your personal data. Three GBs is about right for the base install.

---

### Post by Trurl on 2006-06-13
3 GB was the recommended size, but I don't understand why I'm running out of space on that drive if my personal data goes in the other partition? I have only 387 MB free on the 3GB partition. Do temporary files get stored in / ? Despite having installed some things of modest size, the amount of free space in /home has not changed. I assume that means things are installing in / ? 

Thanks,

Trurl

---

### Post by anaconda on 2006-06-13
All the programs that you iinstall go to root partition to /bin or /usr/sbin or somewhere so 3GB is too small. No wonder it got full fast...

/ should be atleast 10GB. 

Personally I like to keep everything in the same partition.. BUT I keep a few separate partitions to store data, music, movies etc..  SO my /home stays quite small

And I like to keep the size of ubuntu partition at least 20GB... (which isn't much from my 160GB hard-drive

---

### Post by Trurl on 2006-06-13
Thanks for the info! Can I resize my partitions from within Ubuntu? I can give a few gigabytes from /home to / , but I'm not sure how to change the partitions.

I have an XP partition. Could I resize from within XP?

-Trurl

---

### Post by johnc4510 on 2006-06-13
To gain some extra space, probably not much, do this:
Applications>Accessories>Terminal
Type in:
sudo apt-get clean
Hit enter
It will ask you for your password, type it in and hit enter.
Then type in exit, and the terminal will close.
This command cleans up the tar packages used during install, but are not needed now.

---

### Post by johnc4510 on 2006-06-13
To resize a partion, google this:gparted live cd
Download it and burn it to a cd
Put the cd in the cd tray and shut down your computer. Then restart it. The live cd will come up and allow you to resize your partions. The best thing to do would be to take some space from your home partion. I assume it is right next to the root partition. Remember to backup any data that could be lost first.

---

### Post by Trurl on 2006-06-14
I've created the LiveCD and tried to resize the root partition but was unable to. What happened was as follows: 

I have a 3 GB root and a 10 GB /home, in that order (left to right), root and then /home. I also have a windows partition before (left of) the linux root

First, I resized /home down to 6 GB, freeing up 4 GB space. However, the unallocated space appears after /home. 

Next, I tried to add that unallocated space to root but Gparted would let me increase the size of /, saying the maximum size was 3 GB. I have a feeling this has to do with the order of the partitions but I don't know how to fix this, if it is even possible. 

Any ideas?

Thanks,

Trurl

---

### Post by morequarky on 2006-06-14
"I have a feeling this has to do with the order of the partitions"

YEAP

---

### Post by morequarky on 2006-06-14
I have also had a mess of a time with with partitioning because I partitioned not enough space for stuff.

I have to backup everything and move it to another harddrive...than reinstall, then move the stuff back.

Tough.

---

### Post by JazzCrazed on 2006-06-23
Is morequarky's solution really the only one for this situation? I'm in this exact predicament, and I'd really rather not reinstall if I don't have to.

---

### Post by e_james on 2006-06-23
I think it was "gparted" I used on the 6.06 Live / Install CD. There are other partition tools if necessary. Look for a box to specify space before the partition i.e you can resize a partition by moving the beginning rather than the end.

---

### Post by JazzCrazed on 2006-06-23
Already tried that before I posted here using the Dapper LiveCD. It doesn't allow me to put space before the /home partition - only after it.

If it's worth anything, / is on one primary partition, and /home and swap are both logical partitions that are part of a second primary partition. Once I resize /home, I'm only allowed to put space after it, which gets wedged between /home and swap. I can't put the space before /home, which seems to be the key to sucking it out of that primary partition and into / - both Partition Magic in XP and gparted on the Dapper LiveCD are unable to do this.

Here's a screenshot from Partition Magic in Windows: [http://jazzcrazed.com/temp/partitions.png](http://jazzcrazed.com/temp/partitions.png)

C: is obviously XP, M: is /, and N: is /home, with a red sliver at the end that represents the swap (Disk 2 is an external hard drive that I've been using to backup my /home, in anticipation of the partition decimation that I'll probably have to undergo shortly).

Any insight on how to get space from /home to / is much appreciated!!

---

### Post by JazzCrazed on 2006-06-29
Hate to bump, but is there any hope for my partitions? Or should I just nuke the whole thing and start again?

---

### Post by handy on 2006-06-30
If I understand you correctly, the following should work, using PartitionMagic:

***Resize* N:** Taking away however much you want to give **M:**

***_Move_* N:** as far as it will go to the right.

***Resize* M:** Enlarging it into the new free space to it's right!

Does that satisfy, or have I missed something?

---

### Post by drtvasudevan on 2006-06-30
[QUOTE=JazzCrazed]Already tried that before I posted here using the Dapper LiveCD. It doesn't allow me to put space before the /home partition - only after it.[/QUOTE]

you should be trying to resize the extended partition as a whole.
if you try to resize just home it will create space but you cant merge it with root.

i have used bootitng for all my partition works before i got confident with linux itself.
do not install it; just bootfrom it and do a partition job alone.
it allows to create space before the partition or after, either way.
just study it a little bit.
not difficult.

tv

---

### Post by JazzCrazed on 2006-06-30
Nope on both counts... I am not allowed to resize N, and then move N to the right of the unpartitioned space, nor am I allowed to resize the extended partition as a whole, either using Partition Magic from Windows, or from GParted on the Dapper live CD. The option to resize the entire extended partition is greyed out.

Unless *I'm* missing something. Which very likely is the case. And I would have liked to have tried that bootitng...I'll make sure to take a look at it for future reference!

But anyway, I've decided to completely reformat. I've backed up my /home already, and most of my important files are saved on a file server, anyway. Besides, it really seems like the separate partition for / is a bit flawed of a concept, anyway, without knowing how much space will be needed for future software. So I'll be better off this way, I think!

Thanks for your help, though!!

---

### Post by raptros-v76 on 2006-06-30
you know, if you ever decide that you dont need windows anymore, (like i did), then get rid of the windows partition, and use the new space. i personally think that a seperate /home is a necessity, in case you ever need to wipe and start anew. (for instance, a dist-upgrade breaking a system, having a /home allows you to do a fresh install without any qualms)

---

### Post by JazzCrazed on 2006-06-30
I thought about ridding myself of Windows and virtualizing it instead from Ubuntu, but the hassle of activation was enough to deter me (moreso than the thought of reinstalling Ubuntu). I use Windows for Adobe CS2 and for IE, so that keeps it alive on my laptop.

---

### Post by raptros-v76 on 2006-06-30
use the alternate install cd in the future. if i recall correctly, that can resize ntfs partitions

---

### Post by JazzCrazed on 2006-06-30
Actually, so can the LTS CD... GParted works fine for resizing NTFS parts. The main problem is completely subjective in my case -- the 10GB I apportioned to my XP install is very nearly full!

I obviously need to work on my partition size guesstimates in the future. :oops:

---

