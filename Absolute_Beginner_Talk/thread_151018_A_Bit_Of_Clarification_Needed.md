---
title: "A Bit Of Clarification Needed"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Princey on 2006-03-27
I'm not new to linux. However, I still consider myself a newbie as there are countless of areas in linux that I'm new to or haven't even touched. One of such areas has surfaced and while I am pretty much familiar under Windows doing such, I need some clarification as to what I should or shouldn't do and what to expect. 

Here's the dilemna: I dual boot on my main machine with Windows and Kubuntu Breezy. I won't get into the reasons but they're pretty reasonable until I get purchase Win4lin. Kubuntu sits on it's own ide drive, hdb1 (30GB) in size. Seeing I want to replace it with a 120GB drive so that I can run the must-use Windows programs through Crossover, Win or Win4lin here are the questions I need a heads up on:

1. I know to copy my /HOME directory or back it up so I don't have to re-do my aesthetic differences. That I've done. When I install the new drive, do I copy back the settings before or after I do a system update?
2. Which is better, download a fresh breezy iso or use the one I have that came out last October?
3. Grub is written to my mbr on hda1 (a 5GB FAT32 partition). Seeing the drive is going to be changed will the old grub entries interfere or cause problems while installing to the new hard drive? I rather a fresh install than to copy my existing installation.

Thanks for any clarification on the above areas.

---

### Post by meborc on 2006-03-27
for 

1 - i guess it really doesn't matter when you copy your /home folder back to the drive, when you right now have the updated system and you will be installing from new iso (read nr 2)

2 - the fresh iso is the best... cuz then you dont have to upgrade all those xxx packages, which you would, if you used the old cd and then did an upgrade...

3 - when you install ubuntu again (i understood that you will make a new install on the new drive) it will also make a new install of grub, and if all goes well, it will recognize win and there should be no problems there. 

if there are any troubles, let us know ;)

---

### Post by Princey on 2006-03-27
Thanks meborc. I sure will. I'll go at it when I'm back from renewing my driver's license later on.


Update
---------------------
I just checked the bittorrent/iso listings on [http://us.releases.ubuntu.com/releases/kubuntu/breezy/]("http://us.releases.ubuntu.com/releases/kubuntu/breezy/") but all seem to go back to the original release dates. Is that just a glitch in the updating system on the site or it's actually the case?

---

### Post by Princey on 2006-03-28
Just wondering, which file system is best suited for Linux, Kubuntu in particular? I've used the default ext 3 and lvm as well. I remember using Reifer FS when I tried Xandros. What are the differences if any? Any advise or explanations?

---

### Post by IDipSkoalMint on 2006-03-28
I don't really know as this is correct, but when I installed Ubuntu, I originally set it up in Partition Magic as a Linux partition, but a friend told me to delete the partitions (making it just free space) and let the installer do the work for you. Maybe because you're not installing on a partition, that doesn't help, but that's what seemed to work for me. Best of luck to you.

---

### Post by Princey on 2006-03-28
[QUOTE=IDipSkoalMint]I don't really know as this is correct, but when I installed Ubuntu, I originally set it up in Partition Magic as a Linux partition, but a friend told me to delete the partitions (making it just free space) and let the installer do the work for you. Maybe because you're not installing on a partition, that doesn't help, but that's what seemed to work for me. Best of luck to you.[/QUOTE]

I am pretty much aware of that. As stated in my post, I normally let Ubuntu partitioner do the job for me. However, there's also the option to chose your filesystem, whether it's Reifer FS or ext2, ext3, FAT32, LVM among others. My question was whether one file system holds any advantage over the other, if so why and which is best recommended. Thanks for the contribution though.

---

