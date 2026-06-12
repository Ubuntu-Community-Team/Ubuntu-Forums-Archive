---
title: "configuration opinion"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by michalolejarnik on 2007-11-12
I've just installed Ubuntu (latest version) on my Toshiba 1.4 Intel Celeron laptop with 60Gb hdisk, 512 RAM.

I've made the following partitions:

1) created +/- 9GiB for Ubuntu, xt3 partition;
2) created a 2GiB swap partition (swapon), linux-swap partition;
3) left +/- 15 GiB FAT32 for Windows XP, which I will reinstall to have a dual-boot (some of the software I use doesn't run on Linux);
4) and I've left my previous NTFS +/- 26GiB partition where I keep all my files, music, etc.

Does that sound +/- reaosonable?  Or would any of you recommend changes?

Very good expereience with installing the latest version of Ubuntu, no probelms at all, WIFI and all worked right away, need to just tweek Skype to hear my micro, but hope that's a minor problem.

Would appreciate your feedback on the configuration.

Adios,

M

---

### Post by bigken on 2007-11-12
you only need 1gig for your swap

---

### Post by michalolejarnik on 2007-11-12
Grazzie, will do.

M

---

### Post by bigken on 2007-11-12
I think you will need to make an extended partiton as you can only four primeray partitions

install windows 1st the create an extended partition for linux

---

### Post by michalolejarnik on 2007-11-12
Hmm? Sorry, I'm afraid I don't follow

---

### Post by bigken on 2007-11-12
windows will create two partitions the size  you specify and an 8mb one so this will make your partition plan no good as you can only have  four  partitions but if you create an extended partition you can then create more partitions within the the extended partition

---

### Post by erfahren on 2007-11-12
> **bigken said:**
> I think you will need to make an extended partiton as you can only four primeray partitions

install windows 1st the create an extended partition for linux
yep. The other problem is you'd have to re-install GRUB if you install Windows afterwards. It's possible but it's a pain.

You've probably heard that the swap should be twice the size of your RAM. That guideline is actually a little outdated, made when people only had 256MB or whatever. 1GB is plenty. I tried 2GB once and barely used it, kind of a waste of space.

---

### Post by michalolejarnik on 2007-11-12
Ok, I see - so I should redo the installation as follows:

1) reformat the disk (after first backing up the data partition, music, etc.);

2) as the first step re-install Xp creating:

a) one partition for windows (about 15gigs as now), ntfs;
b) one data partition, as now, about 26gigs, also ntfs;
c) one extended partition, which I will use for Ubuntu and the swap partition, which only needs to be one 1 gig;
d) windows will automatically create the fourth, small partition.

3) install Ubuntu, creating one partition for the system and one for the swap.

4) live happily ever after :)

Correct?

Many thanks,

M

---

### Post by robinl on 2007-11-12
I would have a separate partition for /home/ so future reinstallations are easier.

---

### Post by bigken on 2007-11-12
yep you got it :)

---

### Post by michalolejarnik on 2007-11-12
Re post bean 8 - Uh, oh, new, strange input :)
The blue skies have darkened suddenly - need a bit more clarification please :)

Thanks a million guys,

M

---

### Post by iomnipwnedyou on 2007-11-12
impressive!

---

### Post by bigken on 2007-11-12
dont worry about post 8 just make your swap 1gig better safe than sorry

---

### Post by michalolejarnik on 2007-11-12
Excellente, 1 gig for the swap file it shall be.

Many thanks again for the advice, if any of you are in Belgium, I'm offering beers :)

:guitar:

---

### Post by erfahren on 2007-11-12
This is the way I do it:
I install Windows and using its installer I create the NTFS partition I want just for it (like 20GB) and leave the rest free.
Once installed I boot into Windows and use it's Disk Manager to create the FAT32 partition I use for data storage and to share files between the two OSs (like about 20GB).

(I've found that if I created that second partition ("D", I guess) with the Windows installer it makes it extended, using the Disk Manager it can be made a primary.)

I then use the Ubuntu installer to create the rest of the disk space as extended and make the logical partitions:
/
/home
swap

and install.

I've found that works best for me. (I have a recovery partion that's primary as well).

---

### Post by michalolejarnik on 2007-11-12
Oki, doki, sounds like a good tip.  Will go at it tonight.

Adios for now, I owe you guys,

M

---

