---
title: "Partition Madness"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by knottyboy on 2006-08-27
First time in here guys, please be gentle...

Have new Dell laptop with partitions as follows trying to install Ubuntu
dev/sda1 - fat 16 - 47.08mb
dev/sda2 - ntfs - 66.68 GB boot
unallocated - 7.84
dev/sda3 - ntfs - 19.66 GB [empty place for linux]
unallocated - 7.84
dev/sda4 - fat 32 - 3.16 GB
unallocated - 2.19 GB

Now I get that the fat 16 & the first large 67 gig partitions are the windows XP install that I want to keep. The second is a spot to use as backup and is empty and a likely home for Ubuntu. But what the hell is the little fat 32 at the end of the drive? Seems like its with the empty partition for backup. 

The reason I'm asking is that I can't complete my install of Ubuntu untill I have a place for swap. And I'm not sure if I can delete and create a new place for swap without screwing up my xp installation. Any ideas? I tried to create another partion, but only 4 are allowed as primary. 

Thanks for your help in advance.
knottyboy

---

### Post by Metacarpal on 2006-08-28
Hmm.  I have two possibilities for you on the 3.16GB FAT32 partition:

1. I've known many a Windows install to first copy files to the drive, then install, leaving the preliminary copy sitting there for naught.  If that's what you have there, then deleting it would be, depending on your setup when you installed Windows, either completely harmless or utterly fatal to Windows.

2. Possibly your Windows swap/virtual memory?

---

### Post by orb9220 on 2006-08-28
Yeah can't fiqure why you have so many unallocated ones either. But if xp  and ubuntu is all you want then when you start the install from ubuntu and get to manually edit partition table. 

Then delete everything AFTER sda2 so you will end up with one continous unallocated space that will be around 40.69 GB of unallocated space from that you can create a / "root partion of whatever size and a swap of around 500-900 Mb or just 1gb if you want to round up.

Make sure to boot to xp and see what is in that 3.16GB fat which shouls show up as d: in windows.

Also consider making like a 10-15GB ubuntu partition and what's left over make as a large fat32 for storing music,pics,movies,etc... which linux and xp could access.

Just a thought.

---

### Post by bodhi.zazen on 2006-08-28
Not familiar with windows, but...

Sometimes, rather then providing a rescue CD some HW distributors are instead using a rescue partition.

So I have been told.

---

### Post by Metacarpal on 2006-08-28
> **bodhi.zazen said:**
> Not familiar with windows, but...

Sometimes, rather then providing a rescue CD some HW distributors are instead using a rescue partition.

So I have been told.

Ooh - hadn't thought of that possibility.

---

### Post by knottyboy on 2006-08-28
God you guys are great. I've been combing the forums and seriously thinking of starting from scratch with a new windows install if I screw this one up with my partition experiments. So at least I'm getting more encouraged to try linux. Thanks again.
Cheers,
kb

---

### Post by toasted on 2006-08-28
Ive got a new inspiron here with xp.(one month old - 1550) There is indeed a restore partition on it

---

### Post by Metacarpal on 2006-08-28
There you go - dollars to donuts that's your Restore partition.

So if you aren't worried about being able to Restore your initial setup (which, knowing Windows, will completely trash your Ubuntu install), you can probably wipe that extra 3.16GB and use the space.

---

### Post by toasted on 2006-08-28
If you want I will fire it up and see what sizes there are... with windows and the gparted cd if you need....

Edit
Just dont tell the wife  LOL

---

### Post by toasted on 2006-08-28
oops, that cd fell into the drive....  

Booted with GParted tells me this 

fat16  39.19 mib (must be mbr part)
ntfs 38.74 gib
ntfs 12.42 gib
fat32 3.29 mib 
unallocated 7.84

Windows 
C;/ total 38.7
d:/ total 12.4 (backup)

of course there is no mention of the other partitions

Make sure you have your gb and mb labeled correctly
That last fat32 of yours
dev/sda4 - fat 32 - 3.16 GB
may be mb instead of gb?

And the unallocated too
unallocated - 2.19 GB

---

### Post by bodhi.zazen on 2006-08-28
> **Metacarpal said:**
> There you go - dollars to donuts that's your Restore partition.

So if you aren't worried about being able to Restore your initial setup (which, knowing Windows, will completely trash your Ubuntu install), you can probably wipe that extra 3.16GB and use the space.

I have an insider at Microsoft and you can install Windows in  a primary partition without trashing Ubuntu. It will trash the MBR so you would need to re-install GRUB.

> oops, that cd fell into the drive.... 

If you play that Windows install CD backwards you will hear demonic voices worshiping Satan.

Worse... If you play it forwards it will install Windows XP.

---

### Post by toasted on 2006-08-28
> **bodhi.zazen said:**
> 
If you play that Windows install CD backwards you will hear demonic voices worshiping Satan.

Worse... If you play it forwards it will install Windows XP.

LOL - that was the gparted cd though. 
I've never quite dared to play XP backwards and now the rumors are confirmed!!

Is this more insider tips?  Somebody call Martha  :)

---

### Post by toasted on 2006-08-30
Let me know how you make out with this ok? I might have a go at it if you make out good.... The wife will never know  :rolleyes:

---

