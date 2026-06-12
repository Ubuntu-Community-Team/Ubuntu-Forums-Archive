---
title: "Need Help! :S Don't wamt to Loose my Winblows installation."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Cayle on 2007-10-10
Hey there.

Recently i ordered and recieved my Ubuntu and Kubuntu discs from ShipIt.
Currently im running Windows XP. But i would like too run Ubuntu/Kubuntu on the same box.

About 20 minutes ago i tried too go into the Windows install Disc partitioning tool, but i couldnt seem too partition off around 5gb too run Ubuntu on. Now i know you will all be reading this and wondering why am would i want too run Windows in the first place? and i dont blame you. I cant stomach it either. The reason i want too keep my Windows install is that i have many games installed World of Warcraft, Battlefield 2 and Counter-Strike:Source. These unfourtunatly wont run on Ubuntu. (WoW does but its against the ToS of Blizzards too use it on Ubuntu, and i dont want too risk getting banned)

I have a 160 gb Hard drive. so far i still have 70gb remaining. Somehow im not able too partititon off 5gb for Ubuntu. if someone could please tell me how too do this without deleting my current Winblow XP instalation would be great :D 

Cheers!

---

### Post by darren1270 on 2007-10-10
Hi and welcome, first why would you want to use windows partitioning tool????  You can just use gparted on the ubuntu disk.

Steps are pretty easy.

1. Defrag your windows install a few times.... Key is to try and get all your data to the front of the drive.

2. Follow this guide [http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

Good luck.
Darren

---

### Post by om1 on 2007-10-10
good guide 
just make sure you back up all of your data before you start
and burn off your recovery disk (if your computer supports that.... some still come with the recovery disk)
then good luck
post if you need more help

also *most* people here suggest you start off with a dual boot system if you are new to linux.... just so you know....

---

### Post by Cayle on 2007-10-10
Allright thanks guys :)

Sorry about my bad spelling/grammar :S was eating dinner and typing at the same time.

---

### Post by darren1270 on 2007-10-10
No problem..... and as om1 said post back if you have problems.

You'll find everyone here is willing to help you....!

Darren

---

### Post by Angelo DePalma on 2007-10-10
Yeah, the guide says:

"You have to decide which partitions to use or reformat and then use, and where to mount these partitions. You can also resize partitions here, too. If these last couple screenshots confuse you, you clearly need to use either the first or second option."

What if a new user has no ideal "which partitions" are best, "which partitions" need to be "use[ed]" or "reformat[ted]".

The first or second options don't make any more sense.

We need a baby-talk explanation of what we are doing with this partitioning thing, with step-by-step indstructions. NOTHING I've seen on the web (and I've spent about 4 hours looking) explains this properly.

Otherwise, you'lre losing me (and probably tens of thousands of other newbies who do not post to forums).

---

### Post by phr0ze on 2007-10-10
Don't follow any of this. The standard ubuntu install will ask you to pick a new size for your windows partition and it will resize for you. It has never damaged any data for me.

So on about Step 4, pick the option to resize partitions. It will show you a slider. Move the slider to the RIGHT to leave more space for windows. Do not slide the slider to the left, it's already set to the minimum windows needs.

Good luck.

---

### Post by 3rdalbum on 2007-10-10
phr0ze, you should reword your post. Defragmenting from the Windows side is a necessity.

---

