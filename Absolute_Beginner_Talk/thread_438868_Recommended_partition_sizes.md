---
title: "Recommended partition sizes"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-05-10
When I installed Dapper to dual-boot with XP, I wasn't sure I'd want to switch :lolflag: so I just used part of my main Windows hard drive - I wanted to keep my second physical drive for Windows backups. So this is my current setup:

Drive 1hda 38GiB

c:/ Windows Fat - hda3 19.5GiB
d:/ Documents - Windows Fat hda5 6.7GiB
Ubuntu / 7Gib
swap 2GiB
home 3 GiB (4 users)

Drive 2 hdb 38GiB, 32 free

e:/ Backup - Windows NTFS

Now I'm planning to do a clean install of Feisty, and all 4 users are happy with Ubuntu :) so I've decided I might as well use the whole of the second drive (currently Windows e:/ drive) for Ubuntu. We need more space on /home anyway - in home at moment is:
me - 145Mb plus about 1GB still in XP that I'll want to transfer to Ubuntu
other  3 users - 1029MB at the moment, nothing from XP to transfer

So how much space should I allow for the partitions? I know I can leave the swap at 2GiB, but how much should I allow for Ubuntu and /home?

And what will be the safest way to move? I was planning to backup /home, and use the instructions for the clean install, [https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall) 

But if I'm moving to a new physical drive, I suppose I can't do that?

TIA

---

### Post by cotcot on 2007-05-10
I you want the safest way , then make sure you have a backup to a DVD of other media.
Then do the fresh install on the free disk (your e:). Afterwards you could move the existing home using [this]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") howto. 
I suggest 10 GB for ubuntu and 10 GB for home.  This gives 18 GB free for experimenting, backup or moving home.

---

### Post by diskotek on 2007-05-10
2 Gb swap isn't so much?

---

### Post by freesitebuilder on 2007-05-10
> **cotcot said:**
> 
I suggest 10 GB for ubuntu and 10 GB for home.  This gives 18 GB free for experimenting, backup or moving home.

So should I create the 18GB as an Ubuntu partition?

---

### Post by sailor2001 on 2007-05-10
I have a loaded pc including beryl and have only used 13g....just something to go by.

---

### Post by cotcot on 2007-05-12
> **freesitebuilder said:**
> So should I create the 18GB as an Ubuntu partition?
Leave it open. You can make a partition on this unallocated space later. (I use Gparted liveCD for making partitions)

---

### Post by alienexplorers on 2007-05-12
I am running Ubunto on a 40GB drive and have the partitions setup as so:

>  Root   /   15GB
Home     /home    15GB
Data      /data       8GB
Swap     Swap      2GB

I use the Data partition as a place to store Backups of important data.

---

### Post by alchimera on 2007-05-12
re "2GB swap": IMO this is way too much - I know that there are recommendations out there that say that swap partitions should be 1.5 - 2 times your ram, but this comes from the days when 250MB was huge!

I have recently bumped up my ram from 500MB to 1.25GB :), and now the most that gets swapped out is 32MB (out of 750MB) - even under very heavy use; so unless you have a specific use for that much swap, perhaps cut it down to half a gig or so.

[you can type "free -m" in a terminal or use **[conky]("http://conky.sourceforge.net/") **to monitor ram usage]

BTW, i have a full-featured Feisty taking up 5GB of a 7GB partition... all docs/music/movies etc are sitting on other partitions and are shared between several OS's inc. XP, and i don't personally feel the need for a separate /home partition - i *like* doing fresh installs!

---

### Post by freesitebuilder on 2007-05-14
Once I've installed Feisty, can I use gparted to remove my old installation by resizing the Windows partition to use that space?

---

### Post by alchimera on 2007-05-14
> **freesitebuilder said:**
> Once I've installed Feisty, can I use gparted to remove my old installation by resizing the Windows partition to use that space?

yes... but delete the unwanted partition first, then resize.

---

### Post by freesitebuilder on 2007-05-18
> **cotcot said:**
> Afterwards you could move the existing home using [this]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") howto.

I've got my CD, and I've almost got the courage to start, just waiting for the peace and quiet to get on with it! :)

If I move my old home, will that create the three users, or will I need to recreate them?  And should I do that before or after I move the /home?

Thanks for all the help with this - I'm making plenty of notes for next time.

---

