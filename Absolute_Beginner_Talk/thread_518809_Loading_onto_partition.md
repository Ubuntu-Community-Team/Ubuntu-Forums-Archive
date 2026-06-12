---
title: "Loading onto partition"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by colbey on 2007-08-06
Hi all, 

The obligitory im a newbie message should def start this post then i can go to the meat of my problem.

Ive have just partitioned (after a defrag) a bit of my HD, just a gig, to install Ubuntu to see if i like it before going the whole hog. The partition i created as a Linux Swap.

I put in the ubuntu disc, which apparently has no problems according to the disc checker and when my computer boots up i get the ubuntu menu screen. I chose to install/start and it says initialising Kernal, i get two lines of text regarding this then the screen goes blank and i get the following error - 

"Int14: CR2 f8000000 err 00000000 EIP c020c384 CS 00000060 flags 00010003
STACK: c00f7d40 c03f129b 00000002 c00f7d49 000f7d40 00000000 00000000"

I am completely stuck, i tried this on my wifes computer, that thing is old, and i at least get to the brown screen, but then it crashes, tbh I blame that computer as it's about a million years old, but my own one shouldnt have a problem.

If anyone could help me with this i would really appreciatte it. 

Thanks in advance

---

### Post by Inxsible on 2007-08-06
> **colbey said:**
> Hi all, 

The obligitory im a newbie message should def start this post then i can go to the meat of my problem.

Ive have just partitioned (after a defrag) a bit of my HD, [COLOR=Red]just a gig[/COLOR], to install Ubuntu to see if i like it before going the whole hog. The partition i created as a Linux Swap.

I put in the ubuntu disc, which apparently has no problems according to the disc checker and when my computer boots up i get the ubuntu menu screen. I chose to install/start and it says initialising Kernal, i get two lines of text regarding this then the screen goes blank and i get the following error - 

"Int14: CR2 f8000000 err 00000000 EIP c020c384 CS 00000060 flags 00010003
STACK: c00f7d40 c03f129b 00000002 c00f7d49 000f7d40 00000000 00000000"

I am completely stuck, i tried this on my wifes computer, that thing is old, and i at least get to the brown screen, but then it crashes, tbh I blame that computer as it's about a million years old, but my own one shouldnt have a problem.

If anyone could help me with this i would really appreciatte it. 

Thanks in advance

Are you trying to install Ubuntu in 1 GB of drive space?? 

you would need atleast 2-3 GB for the install, not counting swap space, which should be around 1GB.
So in all you would need 5 GB of space

---

### Post by cawill on 2007-08-06
Do you mean that you only created a swap file and no other partitions (like ext3)?

---

### Post by overdrank on 2007-08-06
> **colbey said:**
> Hi all, 

The obligitory im a newbie message should def start this post then i can go to the meat of my problem.

Ive have just partitioned (after a defrag) a bit of my HD, just a gig, to install Ubuntu to see if i like it before going the whole hog. The partition i created as a Linux Swap.

I put in the ubuntu disc, which apparently has no problems according to the disc checker and when my computer boots up i get the ubuntu menu screen. I chose to install/start and it says initialising Kernal, i get two lines of text regarding this then the screen goes blank and i get the following error - 

"Int14: CR2 f8000000 err 00000000 EIP c020c384 CS 00000060 flags 00010003
STACK: c00f7d40 c03f129b 00000002 c00f7d49 000f7d40 00000000 00000000"

I am completely stuck, i tried this on my wifes computer, that thing is old, and i at least get to the brown screen, but then it crashes, tbh I blame that computer as it's about a million years old, but my own one shouldnt have a problem.

If anyone could help me with this i would really appreciatte it. 

Thanks in advance

HI and welcome, firstly 1gig is not enough space for ubuntu, I believe the min is 4gigs. Can you give us some specs on your system like memory, graphics card and so on?

---

