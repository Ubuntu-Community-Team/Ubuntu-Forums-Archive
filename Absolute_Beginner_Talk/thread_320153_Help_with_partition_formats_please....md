---
title: "Help with partition formats please..."
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by PurpleMaestro on 2006-12-16
Hi there,

After several months of viewing these forums I have finally decided to give ubuntu (and hence Linux!) a go… However, I have several questions (below) regarding the set up of the OS and hard drives etc (ever so sorry if I have posted in the wrong area - please feel free to move…). Thanks in advance for any help (oh and sorry for the long post)!

**1) **Ok, first off, my (relevant) system specs are: 

AMD Athlon 64 3800
1GB Ram
ATI Radeon X1800XT (I read there are issues?To think I wanted to have a pretty desktop!)
2 x 40GB hard drives

I had planned to install the 64 bit 6.10 version of Ubuntu, but would I be better off with a different one?

**2)** Second (you guessed it), I want to have a dual boot system (the main reason for posting). This is because I don’t feel entirely ready to abandon Windows XP (I figure that after shelling out money for it I may as well be in a position to use it if I choose) and I do play the occasional game. In addition, I also want to be able to access my data files in both OS’ (this is important!).

I intend to have ‘hard drive 1’ containing both operating systems, partitioned as follows: (Is this a good setup, or do you foresee any problems? Can you recommend a better way of achieving what I want to?) 

25gb Windows XP
14gb Ubuntu
1gb Swap 

(I am presuming that when I start my computer after installing the two operating systems, I will simply be able to choose which one of them I want to access, rather than it defaulting to a particular one?)

Whilst ‘hard drive 2’ will contain all of my music / work files. In order that I can access these files from both OS’, would it be better to use a third party utility such as the one found here: [http://www.fs-driver.org](http://www.fs-driver.org), formatting ‘hard drive 2’ to Ext3, or would it be better to reformat it to FAT32? I honestly don’t understand the pros/cons of either and so your advice is desperately needed! I am leaning towards the latter simply because it seems like so much less hassle, but I haven’t really formed any strong opinions.

Once again, thanks in advance for any light you can shed – I will be eternally grateful!

PurpleM

---

### Post by patrick.dylan on 2006-12-16
Congrats! While I can't answer all your questions, I'll get a few:

- Yes, dual-booting allows you to choose an OS to boot at boot time.
- If you want to access data from XP and linux, then you want FAT, not ext3.
- If you want to have a dedicated FAT partition for data, then yes I would make that fill one of the 40G drives and split the other between OS's. As for the balance of partition sizes, that depends on how much room you'll need for software applications to install on each OS. If it were me, I'd do 20/20, but YMMV.
*Edit: You are correct that you need both a root partition and a swap partition for linux. Sorry if I was unclear. *

---

### Post by Bachstelze on 2006-12-16
> **patrick.dylan said:**
> 
- If you want to access data from XP and linux, then you want FAT, not ext3.

Wrong. There are fully functional ext2/3 drivers to use in Windows. Plus, FAT32 has a 4 GiB per file limitation.


> **patrick.dylan said:**
> *Edit: You are correct that you need both a root partition and a swap partition for linux. Sorry if I was unclear. *

Not true. Though it is indeed recommended to have a swap partition, it is not absolutely required and running without one is perfectly possible.


As far as the ATi card goes, there are indeed issues with them due to drivers not as functional as nvidia's but with some work I think it can be solved.

And you can run the 64 bit version if you want but you might end up with software incompatibilities, especially with proprietary stuff (Flash Player among many others), so I think you'll be more comfortable with the 32 bit edition, it won't make much difference performance-wise anyway.

---

### Post by patrick.dylan on 2006-12-16
> **HymnToLife said:**
> Wrong. There are fully functional ext2/3 drivers to use in Windows. Plus, FAT32 has a 4 GiB per file limitation.




Not true. Though it is indeed recommended to have a swap partition, it is not absolutely required and running without one is perfectly possible.



I stand corrected!  :-#

---

### Post by PurpleMaestro on 2006-12-17
Ok, so i will use the standard 32 bit version - its not like I really need the 64 bit I suppose...

But, which setup would you recommend ,hymn (or others)? Does one have a lot of advantages over the other? The 4gb file limitation won't be too much of a problem for me as I don't plan to have any this size. (I am however on a rather large network and so security is an issue)

Thanks for helping!

---

