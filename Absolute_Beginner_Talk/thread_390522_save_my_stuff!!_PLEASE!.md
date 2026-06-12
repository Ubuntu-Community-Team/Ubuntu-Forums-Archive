---
title: "save my stuff!! PLEASE!"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by bob dylan on 2007-03-22
hi all!

i would like to say that i am falling in love with my virtual version of ubuntu 6.10!!! BUT...

i have now tried to install it as my official OS, and i have hit a hurdle :(

i have windows XP on the C: and my personal files on the G:

my goal was to install ubuntu on my C: and retain my personal data on the G: (keep in mind that there is only one physical drive in the PC), but i ran into a potential problem where ubuntu wanted to reformat my entire physical drive!!!

first off, i really don't want to backup all of my personal data on the G: because there is over 100GB of it!!

please someone help me because windows is eating my soul!!!!!!!!

thnks.

- michael

---

### Post by Shatrat on 2007-03-22
What you need to do is defrag whatever partition has the most free space on it, and use the manual partitioner on the liveCD to resize that partition and then create a swap partition of about 1.5 times the size of your ram and the rest partitioned and formatted ext3.

And if you dont have the stuff backed up, it's only a matter of time till you lose it.  Hard drives do die.

Here is a nice install guide you might want to check out, especially the partitioning bit.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by igknighted on 2007-03-22
:) When you get to the partitioning stage, do not choose automatically partition.  When gparted open with the manual partition setup, you can delete the "c" drive (make sure you know which is which, probably by size... don't go by position on disk necessarily.  Also, the "c" drive partition should be flagged as bootable.  So, delete that partition (assuming you are getting rid of windows, thats the impression I got).  Then (if you have 2 or less remaining partitions) create a 1gb or so swap partition (swap is in the file-system drop menu) and the rest an ext3 partition (and set the mount point as "/", without the quotes).  If you have 3 partitions on the drive before the Ubuntu ones, you will need to create the linux partitions as extended partitions, as only 4 primary partitions are allowed on one disk.

---

### Post by justleen on 2007-03-22
just a small addition: once you have done the manual partitioning, and Ubuntu gives the overview of which drives will be used, there are ticks behind the drives for Reformatting. Just double check your data partition is not checked, and your in the clear.

---

### Post by kinson on 2007-03-22
Just to add on something. Since you've been running windows xp, I'm guessing that your data drive (G) is formatted in NTFS.

Ubuntu doesn't natively write(but can read) to NTFS drives. There is a third party driver to write to NTFS drives, but as far as I know, its still in BETA or something, so I wouldn't recommend it.

So you might have to backup your files in your data drive and format it to another type of file system that linux supports (ext3, FAT32, etc etc). I'd suggest ext3.

just my 2 cents.

Cheers,
Kinson

---

### Post by bob dylan on 2007-03-24
i just want to thank all you fellow peeps for the quick response!!!

this has been my first ask-for-tech-assistance post and i must say that i am amazingly supprised at how quick y'all responded!!!!! ++

and thanks for everyones help; i will be removing windows from my soul so that i can enjoy the free world in peace!!!!

THANKS UBUNTU!!!!

ps: i will keep everyone posted on my ups and downs.

:guitar: 
be cool.

---

### Post by lamalex on 2007-03-24
a note on the the ntfs drivers, they are no longer beta and are very stable and reliable. if you can ever convert that partition to ext3 or some decent file system you will benefit, but for now the drivers called "ntfs-3g" are very stable.

---

### Post by kinson on 2007-03-24
> **Iamalex said:**
> a note on the the ntfs drivers, they are no longer beta and are very stable and reliable. if you can ever convert that partition to ext3 or some decent file system you will benefit, but for now the drivers called "ntfs-3g" are very stable.

Thanks for the update :)

Cheers,
Kinson

---

### Post by bob dylan on 2007-03-25
good evening everyone!!

i am back and i would like to say that right now it is 1am my time (here in houston tx) and i would like to officially announce here at the ubuntu community forum that i am posting my last post from a microsoft based PC. ok well it may not seem like a big thing for alot of you people who have been using linux for a while... BUT this is a MASSIVE switch for me, and yes... this is going to be an awesome ride!!!!

thanks again for all the help and astala-VISTA microsofty!!!!

ps: i will post here again later on this morning from my brand new ubuntu 6.10!!!

again thanks everyone for the great support!!!!!!

- bye

---

### Post by lamalex on 2007-03-25
Unfortunately there is no ubuntu smiley with a party hat or I would post it. but. CONGRATS MAN!!! Welcome to the club, tell your friends, spread the word, and whenever you need help, we're always here to help out!

---

### Post by rodrigo juarez on 2007-03-25
=') That's the spirit!

Don't forget to check : [http://ubuntuforums.org/showthread.php?t=232059]("http://ubuntuforums.org/showthread.php?t=232059")

---

### Post by bob dylan on 2007-03-25
i am in the world of UBUNTU!!!

thanks everyone!!!

bye for now, it's time to explore!!

---

### Post by bob dylan on 2007-03-25
i would like to say that i have been using UBUNTU 6.10 for about 1 hr 30 mins, and all i can say is YES!!!!!!!

i am soooo happy right now!!! even though i lost my main menu bar (the one with everything on it...ya no the clock, apps, places, system...etc... HAHAHAHAHAHAHAHA) i'm ok now though, i learned how to build my own custom one....

(no rules to abide by like windows has)

well, i'm off now but i will be back to the ubuntu forums from now and ever more.

thanks everyone!!!!!!

oh, and just another quicky two-cents... i want to shout out to all those people "pushing an shovin" (thanks tools :guitar: ) open source in south africa. i am originally from there, and i know that there are lots of issues with computer access in south africa, and i recently read about some people building ubuntu powered PCs to give some unfortunate schools there the magic of computing that we all enjoy so freely:

"Y'all are awesome!!!!"

ps: i will try and find some links to your work on the web to post.

- laters all, and thanks again for the quick response to my previous queries.

---

### Post by bob dylan on 2007-03-25
hi everyone... it's me again!

well i have hit a problem. i have been trying to access a partition on my harddrive, (sda5), but unfortunately it will not let me change anything on it. (i think that it's read-only)

please can someone help me, it's all my personal stuff and i can't change any of it !!

thanks so much!!

- michael

---

### Post by jeffathehutt on 2007-03-25
If the partition you are trying to access is formatted with NTFS, take a look at [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

ntfs-3g is a driver for linux that allows you to read and write to NTFS partitions.

---

### Post by bob dylan on 2007-03-25
it is NTFS, so i will try what you suggest!!

THANKS, YOU'RE AWESOME!!!!!

---

### Post by jeffathehutt on 2007-03-25
Just one general caution...

You really should backup your files.  Hard drives certainly don't last forever, and one hard drive crash would wipe out all your data...

---

