---
title: "Dropping my Windows Partition"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by rlynch on 2006-11-01
So here's my setup.

I formatted my laptop 2-3 months ago. Going from windows xp to 2000. I made a 8 gig partition for the windows. and the rest went for things I download.

I decided to do a duel boot, so resized my big download partition, and made a seperate 10 gig partition. So my hdd is in this order '8 gig partition for windows(ntfs)', then a '40 gig partition for downloads(ntfs)', then my 'two ubuntu partitions 9 for / and 1 for swap'.


I'm done with windows on the laptop. I have 2k on my desktop for games, and that's all I need it for. My question is as follows.

Is there a way to reformat the 8 gig and 40 gig ntfs partitions, change it over to ext3 and not have to wipe my current install clean? Or do you think with the / parition coming so late in the hdd(it's 40-50 gigs into it) that I could do better wiping the entire thing clean and installing fresh?

---

### Post by blendmaster on 2006-11-01
I think you **have** to start fresh.

Combining partitions in general is impossible without reformatting.

Backup your stuff, insert the Ubuntu live CD, and run the installer.

The backing up part is the hardest thing you'll have to deal with.

---

### Post by rlynch on 2006-11-01
im copying my data in the downloads partition to my desktop now via ftp. soon as i reinstall i can copy the data over, but just need to reinstall the software again

wish me luck. . .if anyone else has any tips/suggestions, lemme know

---

### Post by mo79 on 2006-11-01
Hmm, don't quote me *too* concrete here (not been using Ubuntu long myself), but you could (after backing up!) perhaps delete the relevant partitions and resize the Ubuntu ones with GParted?

---

### Post by bruenig on 2006-11-01
Not certain this could work. If it is a possibility, as you seem to imply it is, I would just fresh install.

---

### Post by rlynch on 2006-11-01
Yea, I don't mind doing it, as long as it runs the way it should. If there's anything that could go wrong, or not run right by redoing the current parititons, I don't mind doing a fresh install.

I have my kubuntu disc here, so I'll try that. If it installs correctly I can go from there, but for some reason I only get 2-3 installs from a cdr of ubuntu. And i've used those up by trying to get 3d accel for xgl on an ati card. But I'm past that now.

---

### Post by mattskr on 2006-11-01
I've never done it with Gparted but...Gparted is a clone of Partition Magic for Windows....

With Partition Magic you could delete those two partitions, then resize your Ubuntu partition.

It will have to move all your data including your boot loader. So you'd have to reinstall GRUB (or whatever you use) to be able to boot. But hey if it doesn't work just reinstall :)

---

