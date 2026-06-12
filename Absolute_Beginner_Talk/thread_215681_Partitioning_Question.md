---
title: "Partitioning Question"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by smokeysaysno on 2006-07-14
I've decided for my computer to get rid of my windows partition completely and have strictly use linux.  What would be the best way to partition my hard drive? I want to be able to have enough room on my first partition for linux and its programs and also have a partition that can hold everything else.  That way I won't have to put my music and files on after reinstalling or reformatting my linux partition.  I have an 80gig HD.

---

### Post by molly_001 on 2006-07-14
Do the text installer, using the Alternate Install CD for Ubuntu (don't use the LiveCD installer.)

20GB will be enough for the partition containing the linux install.
Then you will need a separate /home partition to put all your data onto it -- this will always keep your data safe in the event you wish later to change your linux install.

And finally, your SWAP partition which will need to be 1.5x the size your RAM.

So:
a>  Ubuntu install partition 20GB
b> separate /home partition 58GB
c> SWAP partition 2GB or less

An excellent guide for the text installer and what you wish to do is here (obviously, ignore the NTFS references/sections) :
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by T700 on 2006-07-14
Check out this [excellent guide]("http://psychocats.net/ubuntu/partitioning.html") by one of our very own forum members.

Paul

---

### Post by Sonofmoog on 2006-07-14
If it were my system, I'd do it like this:
/        9 GB
/swap    1 GB  (2 x RAM is recommended)
/home   70 GB

though I'd be tempted to split the home partition, and put my music into its own partition.  A 9 GB root filesystem will give you enough room for all the packages and desktops you might reasonably want ..

---

### Post by smokeysaysno on 2006-07-14
Thanks, those are both great replies!  One more question though, is it possible to make a partition my home folder after i've already installed everything onto one big drive?  When I installed I just chose the automatic partition option so I have a 78 gig linux partition and a swap.

---

### Post by smokeysaysno on 2006-07-14
Thanks for the help everyone.  I actually found the answer to my last question on the website you gave me.  

[http://www.psychocats.net/ubuntu/separatehome.html]("http://www.psychocats.net/ubuntu/separatehome.html")
Once again, thanks!

---

