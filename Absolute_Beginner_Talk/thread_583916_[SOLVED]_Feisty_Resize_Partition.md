---
title: "[SOLVED] Feisty Resize Partition"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-10-20
When I was installing my first try of GNU/Linux, I chose Ubuntu Feisty. That was about three weeks ago. I had just bought a bunch of parts for a computer, put it together over the course of a couple of hours, and set up the BIOS. It was the first time I made a computer. However, I was getting tired. I put in the CD that I had downloaded over the course of a couple of days and ran Ubuntu off of the CD. Happy with it within the first 30 minutes, I tried to install it, only to find out that I had to partition my hard drive, which was something I saw coming. I tried to split my 250GB hard drive in half, not including the swap - which is something that I don't know about at all - and came across numerous errors. Since I was tired, my patience was a bit lower than normal. After about half an hour of trying to partition my drive, I settled for only 5GB of space, and went to sleep.

I have now encountered a problem - I have run out of room. I thought that partitioning the hard drive like that would allow Ubuntu to take up the remainder of the hard drive, not the 5GB that I allocated for. I have also heard that to repartition a drive is supposed to be very dangerous, which I do not mind facing in the slightest. If someone would be able to help me with this I would be greatly appreciative as I have come to really like using Ubuntu over Windows... GARBAGE!

Thank you for your consideration.

---

### Post by mikewhatever on 2007-10-20
Repartitioning a drive is not really that dangerous unless you are not afraid of loosing data. Backing things up comes as a handy solution here. You should be able to repartition quite easily using [Gparted]("http://gparted.sourceforge.net/") from the live cd. The [DOCUMENTATION]("http://gparted.sourceforge.net/documentation.php") is quite good there.
If you want more specific help, post a screenshot of your partition table, or the output of fdisk -l, and specify your current goals. It matters a lot whether you want to reinstall or stick with Feisty, etc.

---

### Post by ShadowMKII on 2007-10-22
Ah, that documentation was quite good - and reasurring! However, I was unable to run Gparted off of the LiveCD that I downloaded earlier. I even had it installed on my computer and tried to do some resizing there, but to no avail. I managed to resize the swap portion of my drive due to its lack of size, but that was it, seeing as how my ext3 room for Ubuntu was unable to be edited due to its mount point "/." Any ideas?

---

### Post by ShadowMKII on 2007-10-25
Anyone out there?

---

### Post by Doggles on 2007-10-25
Hi ShadowMKII,

The reason you can't mess with partitions using an installed version of gparted is because in order to partition a drive, that drive must not be mounted (and when you boot from your hard drive, your hard drive gets mounted and must stay mounted) - that's why folk usually run gparted from the live CD (the hard drive doesn't need to be mounted as everything is running off the cd, and therefore the HD can be edited successfully). How about this - you can either boot from your ubuntu live cd and then try to download and install gparted with synaptic that way? - I'm at work at the minute so I can't try this out for you to verify if it works.

Also - you say you don't know anything about the swap - the swap partition is a small area of the disk that linux needs to use as a sort extension of the physical memory - a kind of "dumping ground" where stuff can be stored if physical memory is full. It doesn't need to be very big - most people seem to recommend setting the size of the swap to about twice the size of the RAM in your machine - so when you do finally get into gparted and get this sorted out, set your swap to an appropriate size.

If you don't mind losing all the data on your disk (which if it's only been running for 3 weeks is possible I suppose, then you could reinstall and use the "use whole disk" option - probably easiest for beginners.

Cheers mate - and good luck

---

### Post by Doggles on 2007-10-25
.... oh and by the way - when using gparted you might have to unmount disks if they have been mounted before you partiton them -  if they appear on your desktop, then right click and "unmount"

---

### Post by ShadowMKII on 2007-10-26
I have everything solved now! I had to change the boot order for my devices on my computer so that my CD Drives booted first, before my hard drive, and that is how I got the LiveCD to work! I have it all partitioned nicely and evenly now, have lots of space, and have upgraded to Gutsy without a problem! Hooray, and thank you for your help! ^-^ Your detailed advice was most appreciated!

---

