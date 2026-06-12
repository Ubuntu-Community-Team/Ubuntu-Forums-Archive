---
title: "[SOLVED] Confused about dual boot installation"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by bananab on 2008-05-27
Hi, I'm new to both Macs and Linux. I'm trying to dual boot OS X with Hardy on my my 4th generation (Penryn) MacBook Pro. I followed the dual boot instructions at [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
and ended up with OS X and then two partitions with Ubuntu on them (I have the option to boot from Linux on Partition 3 or 4 on my rEFIt menu). Can someone explain to me why the above article has you installing Ubuntu multiple times (once in the "Preparing to Install Ubuntu alongside OS X (Dual Boot)" and again in "Ubuntu Installation (Dual Boot - OS X)")? Also why is step 3 of "Ubuntu Installation (Dual Boot - OS X)" having me cut sda3 into two individual partitions? 
Thanks a lot, Jeff

---

### Post by stueng on 2008-05-27
Hi Jeff, I am not about to read through that entire tutorial to try better understand your questions but I will have a go at guessing based on past experience - in fact its not even loading for me at the moment

1) Are you sure the second Ubuntu option isn't the bootable Ubuntu CD?
2) Perhaps you read instructions on two different approaches to installing Ubuntu?
3) You need to split the /dev/sda3 into two partitions because linux needs at least two partitions to operate - one for swap space and the other for your data - linux does this to increase stability as it stops your operating system from running out of space in swap area should you fill your hard disk

I have created some instructions on dual booting Ubuntu and Mac OS X and tried to explain things a little bit more in depth than you find in most tutorials - I would be obliged if you give them a read and post back any comments to me

[http://www.lostpeg.co.uk/content/view/27/68/]("http://www.lostpeg.co.uk/content/view/27/68/")

---

### Post by stueng on 2008-05-27
That page finally loaded for me... yes it seems the same page contains instructions for installing Ubuntu in more than one manner (Dual boot, tripple boot etc) you should only follow one set of instructions

---

### Post by buschi on 2008-05-27
hey jeff,

i had a similar experience on a 2nd gen macbook. however, in rEFIt, i could choose between "start linux from HD" and "start linux from partition 4". that's not the case for you, right?

however, what did the trick for me was: where they recommend to choose (hd0,3) in the end, i clicked on the drop-down menu and selected /dev/sda  (meaning that you have to install ubuntu again).

actually, it seems that you do not /have/ to make a swap partition, on wikipedia there is a not saying that having a swap-file is just as fast -- however, a swap-partition is just the way folks got used to :) it's like an extension of your RAM.

good luck! (after the installation, things will get easier ;)
sebastian.

p.s.: the installation should actually not differ that much from a macbook: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by bananab on 2008-05-27
stueng, the seeminly duplicate instructions that i'm reffering to aren't from the Dual to the Triple boot instructions, they are between the "Preparing to install" and actual "Ubuntu instalation" parts of the dual boot guide. Thanks for the link to your tutorial though. I'll give that a try this evening. And thank you both for your quick responses.

---

### Post by cyberdork33 on 2008-05-27
you do not need to install twice... it sounds like there is an error on the wiki page.

you have to have a swap partition for hibernating, but if you don't plan to use that, a swapfile is just as good.

The install process is pretty much the same for any mac, so referencing other guides (even for other Mac types) should be ok.

---

### Post by bananab on 2008-05-27
Thanks everyone.

I got it up and running!

---

