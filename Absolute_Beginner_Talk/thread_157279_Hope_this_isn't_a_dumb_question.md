---
title: "Hope this isn't a dumb question"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-04-08
What is a swap partition.  I see it all the time, like today when I was trying to install SusE on a computer and it told me my hard drive did not have enought space for the swap file.](*,)  Can some one tell me what swap does?

---

### Post by 5-HT on 2006-04-08
Swap is used as a sort of 'harddisk pseudoRAM' when you run out of physical RAM (same thing as  page files in windows).
As it runs off the harddrive, using swap is much slower than RAM, but it beats running out of RAM.

A good rule of thumb for swap size is ~ 1.5 - 2 x RAM.
If you have lots of ram though, you can decrease this number. If you only have a small amount of ram it's better to stick with around swap = 2 x RAM.

HTH

---

### Post by eriefisher on 2006-04-08
It act as extra memory should you need it. If you run out of memory especially with lower memory machines, you can use disc space. There is alot of debate on how big /swap should be and whether or not it is needed with systems with alot of memory (over 1g)

eriefisher

---

### Post by catlett on 2006-04-08
What size hard drive were you installing on? The swap will be similar to a Ram size. 256 to 512MB. Is your drive under 2 gigabytes? 2 Gigs is enough to install a basic OS with a moderate swap?

---

### Post by NeoGreen on 2006-04-08
I was trying to install SuSE Linux on a Dell Dimension Desktop, Pentium 3 and 20 gigs hard drive.  It originally had Windows 2000 Pro installed but I wanted to delete it and install SuSE instead.  When I repartioned the hard drive (using a XP install disk to repartion) and I ran the SuSE install disk it gave me an error message tell me there was not enough memory swap memory for YaST.  I don't understand why it would say that when I reformatted the hard drive and it's empty.  ](*,)

---

### Post by catlett on 2006-04-08
That's a perfect first Linux machine. Have you resolved the problem? If you haven't, the problem is that the drive probably didn't get formatted correctly after it was erased. If the formatting is junk the disk will be read as full. Therefore the prompt about no room for swap. It's just like when you put a CD in that isn't any good but you know there is nothing on it. The computer will read it as full and no room is free.
If you want to use that disk the Ubuntu install shouldn't have a problem erasing the drive and reformatting. Just choose the first option during install. "Erase entire drive and use for installation".
If you've solved the problem and were just curious about swap, disregard.

---

### Post by NeoGreen on 2006-04-08
No, I have not solved the problem yet, I will use the ubuntu install disk to format the hard drive then run SuSE.  Can I do that?:rolleyes:

---

### Post by franklee on 2006-04-08
Someone once told me to have no more than twice the physical ram in swap. So 256meg of ram becomes 512meg of swap...usually at the end of the drive, is my preference. Suffice to say there seems to be a lot of debate about how much swap is needed for faster transfer ram, like ddr2 and ddr for pcs. My hacking buddy swears by double and no more.

ah well

---

### Post by franklee on 2006-04-08
yeah no problem with a suse install after an ubuntu cfdisk (which occurs during default installation. I would recommend you familiarise yourself with fdisk or cfdisk when you get a chance as they are handy partitioning tools to use, cfdisk in particular is very user friendly.

---

### Post by catlett on 2006-04-08
The install can erase and format the drive during install, and I guess you could stop the install after the partitioning. But if you are going to use Suse after I would do one of two things. 
If you have the Live CD version of Ubuntu use that. Boot to the cd like it was an install disk. The setup of Ubuntu will run and Ubuntu will run from the cd. Once in the Ubuntu desktop you want to use the Ubuntu partitioner gparted. Open the terminal and type ```
sudo gparted
``` This will start gparted. From there you can partirion and format your drive. Log out. Replace Ubuntu Live with the Suse install disk.
The second is to let the Suse install disk do the formatting. I'm not positive about the choices when installing Suse but I would bet there is a choice to erase entire disk and use it for the install. I would try this first anyway. If there aren't any choices when the partitioner runs, look for an option to manually edit.
Throw the Suse disk in and run it. Pay attention to the partitioner and let it have the whole disk. I'd bet it was a bad format by the Windows disk and Suse wil install fine if you have it erase the entire drive and install on it however it wants. Good luck.

PS It's easier than you think. You just got stuck because a couple of billionaires don't care about dedault utilities in their systyems being 1st rate. Regards

---

### Post by 3rdalbum on 2006-04-08
Allocate as much or as little swap space as you wish. If your current RAM usage is greater than the swap space, Ubuntu just uses the other parts of the disk for swap. (my swap partition is actually the same size as my real RAM - I assumed the installer knew what it was doing :)  )

Try not to use more than 1.5 * your memory, because performance is decreased further after that.

---

### Post by NeoGreen on 2006-04-09
Thanks for the info, I'll try it right now:) Looks like I'm going to have to run to the store and buy me a 12 pack of cokes and some sour worms:D

---

