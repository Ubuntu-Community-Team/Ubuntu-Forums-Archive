---
title: "Tried installing Ubuntu on my intel iMac"
date: 2006-07-20
forum: Apple PPC Users
---

### Post by Tonks on 2006-07-20
I have an intel iMac 17" and i wanted to install ubuntu to try xgl and to just try an other OS sometime. So i found [this](http://www.planetisaac.com/articles/ubuntuinstall.html) tutorial and it seemed pretty easy! But then i was at the "liloconfig" file but then i did the 3dd stuff and then all blue ~ ~ ~ appeared and i paniced and then i closed the terminal window! And i was like "Damn!" but then i tried to liloconfig again but i could not.

So i tried to format the partition (i made a 9500 drive and a 500 swap) but i deleted them and then i wanted to make them again but it said "Unknown file system and a sort of black square and so now i can't restore the drive in OS X and can't make partitions in Ubuntu and i can't install windows on it

So can anyone please help me with this issue, i would love to use Ubuntu on my intel iMac.

---

### Post by aronhjarta on 2006-07-22
Mmmkay,

I did the same thing and followed that tutorial to the letter.  I found that there is an error towards the end of the document : 

lilo -b /dev/sda3 

It should have been 

lilo -b /dev/sda 

I did it the wrong way around at first, and refit didn't see the partition as a linux penguin after I synced the partition tables.  It became obvious after I tried booting the "legacy os" icon through refit and all I got was a black screen that said "Missing Operating System".  It was around that time I realized something might be slightly askew.

Eager to get my nose bloodied again, I promptly turned my machine off, whacked the dapper ubuntu live cd into the drive and held down the c button.  Started the live ubuntu again, but did NOT redo the install.  I simply opened up 2 terminals.  

In one I ran parted to make sure that all the partition info was right.  In my case it was sda3 boot on.

In the second terminal I repeated the mounting of the /mnt/ubuntu and proc and dev and did the chroot to work on the disk.  Then I ran 'lilo -b /dev/sda' - I did get an error  (ish) message, but it wasn't as hostile as the one I had before with 'lilo -b /dev/sda3' 

exit the chroot environment and umount the /mnt/ubuntu/dev, proc and ubuntu

reboot

after this everything worked a treat.  Refit saw no "legacy os" partition, but rather a handsome little penguin icon.  schweet.  Hope this helps.


> **Tonks said:**
> I have an intel iMac 17" and i wanted to install ubuntu to try xgl and to just try an other OS sometime. So i found [this](http://www.planetisaac.com/articles/ubuntuinstall.html) tutorial and it seemed pretty easy! But then i was at the "liloconfig" file but then i did the 3dd stuff and then all blue ~ ~ ~ appeared and i paniced and then i closed the terminal window! And i was like "Damn!" but then i tried to liloconfig again but i could not.

So i tried to format the partition (i made a 9500 drive and a 500 swap) but i deleted them and then i wanted to make them again but it said "Unknown file system and a sort of black square and so now i can't restore the drive in OS X and can't make partitions in Ubuntu and i can't install windows on it

So can anyone please help me with this issue, i would love to use Ubuntu on my intel iMac.

---

