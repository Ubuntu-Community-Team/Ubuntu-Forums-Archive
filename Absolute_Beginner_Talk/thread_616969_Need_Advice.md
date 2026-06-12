---
title: "Need Advice"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Uberuntu on 2007-11-18
k so i just formatted my hard drive and partitioned it as follows (used partedmagic)

1) 5 gigs (ext3)boot - and i made this the root dir
2) extended partition
3) 2 gigs (swap)
4) 210 gigs (ext3)- and this is supposed to be where i keep my files

ok so now i logged into gutsy and everythings cool, the big drive is there on my desktop, but i cant write to it and it has the lost and found folder in it.

Can someone tell me what i did wrong and also tell me how to make all the programs that i install go to the big partition instead of the one the root is in. THNX :)

---

### Post by RockTonic3 on 2007-11-18
you should have used the big drive as the root?  this is the equivalent of the C: drive in windows i'm pretty sure, so it's the default for all system files and stuff to go.  I can't imagine that you can change the root directory now that ubuntu is installed, maybe it would be easier to start over?  use gparted in the ubuntu repositories to partition the disk.  it's available during setup if you choose the option to manually partition the disk.

---

### Post by Uberuntu on 2007-11-18
i want my files to be seperated from the OS. I heard that the best thing to do is to make you boot partition about 2 to 5 gigs so you can have room for upgrades. Then all your programs and files go on the big partition. I may be mistaken but i think this is a pretty good idea.

---

### Post by LaRoza on 2007-11-18
> **Uberuntu said:**
> i want my files to be seperated from the OS. I heard that the best thing to do is to make you boot partition about 2 to 5 gigs so you can have room for upgrades. Then all your programs and files go on the big partition. I may be mistaken but i think this is a pretty good idea.

No, / will have the programs, but /home will have your personal files and settings.

---

### Post by RockTonic3 on 2007-11-18
well, what i usually do is leave about 10 gigs for the root partition, which seems to be enough for system files and additional packages.  after that i have about a 15 gig partition for xp, and the rest is FAT32 so that i can keep my music and documents on it and read/write from both operating systems. I'm not sure how to go about installing packages and whatnot on a separate partition, I'd think this might slow things down a bit?  maybe not.   

it does seem like a good idea, in that if you ever need to reinstall ubuntu you won't have to find all the packages again, but i think there are better ways to do that if it's what you're trying to do.  the program APTonCD for example will let you burn all of your installed packages (not native to a fresh ubuntu install) onto a cd or dvd, then you can easily install them all again on a fresh ubuntu.

---

### Post by LaRoza on 2007-11-18
> **RockTonic3 said:**
> well, what i usually do is leave about 10 gigs for the root partition, which seems to be enough for system files and additional packages.  after that i have about a 15 gig partition for xp, and the rest is FAT32 so that i can keep my music and documents on it and read/write from both operating systems. I'm not sure how to go about installing packages and whatnot on a separate partition, I'd think this might slow things down a bit?  maybe not.   


10-15 GB is good for /. FAT32 isn't a really good format, Ubuntu has NTFS write support now, so use that for sharing.

No, having /home on a different partition doesn't slow anything down.

---

### Post by Sims2789 on 2007-11-18
> **Uberuntu said:**
> k so i just formatted my hard drive and partitioned it as follows (used partedmagic)

1) 5 gigs (ext3)boot - and i made this the root dir
2) extended partition
3) 2 gigs (swap)
4) 210 gigs (ext3)- and this is supposed to be where i keep my files

ok so now i logged into gutsy and everythings cool, the big drive is there on my desktop, but i cant write to it and it has the lost and found folder in it.

Can someone tell me what i did wrong and also tell me how to make all the programs that i install go to the big partition instead of the one the root is in. THNX :)

I just have a main drive and a swap drive; it simplifies everything, even though it may be less technically meritorious than having three partitions.

As for format, ext drivers for Windows exist, so just put the driver on the Windows machines you share files with, or make an NTFS partition and manually put the files you want to share in there. You may have to grant yourself read/write permission for this drive, though.

---

### Post by antoz on 2007-11-18
I would increase the root partition to about 10GIG and then make the bigger partition into a separate "home" partition this is where all your file and settings will be kept a bit like My Documents in Windows.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

