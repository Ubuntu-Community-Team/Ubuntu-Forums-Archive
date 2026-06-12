---
title: "Install hanging"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Spaaarkz on 2007-03-15
Hello,
I am hoping someone can help me as I am totally stuck.
I am trying to install ubuntu onto my laptop - it currently has xp on it and I want to make it dual boot. However, whenever I try to install ubuntu it is hanging when I choose to manually partition the drive. The partition programme opens and the clock come up but it goes not further. 
I tried to install ubuntu before and got past this stage, but I cancelled out further on in the process as I did not have time. It is just now, when I try again that I am getting this problem. I have tried another install disk but the problem remains.
Any suggestions?
Cheers,
Spaaarkz.

---

### Post by rusty4r on 2007-03-15
Still pretty newbish myself but did you run the check media option at the beginning of the bootup?

---

### Post by Spaaarkz on 2007-03-15
Is that the check cd at the boot menu? I have run that and it checked out fine......

---

### Post by starfleetcaptainrob on 2007-03-15
Are you using a CD that you burnt from a downloaded ISO image?  If so how fast did you burn it?  If you burnt it any faster than 4x then it's likely the CD is unstable it's self.  The same thing happened to me.  I went and reburned at 4x and it installed perfectly the next time around.:guitar:

---

### Post by oilchangeguy on 2007-03-15
it's easier to simply let ubuntu use the largest unused part of the drive. this will pretty much split the drive in half. xp on one half and ubuntu on the other half. no need to do any manual partitioning.

---

### Post by Spaaarkz on 2007-03-15
> **oilchangeguy said:**
> it's easier to simply let ubuntu use the largest unused part of the drive. this will pretty much split the drive in half. xp on one half and ubuntu on the other half. no need to do any manual partitioning.

Problem is the only option I have is to reformat my hard disk entirely (which I don't want to do as I want to keep xp for the time being) or manually partition the drive - I have 1 hard disk which has been partitioned into 2 drives - the second partition is where I want ubuntu installed. 

I will try burning the disk again at a slower speed - though I am not sure if this will help. The first time I tried installing the disk worked fine - it is now it is not working. I have tried a second disk with the same problem. 

My pet theory is that the aborted installation I tried originally has done something to the partition which is causing problems this time around.....I think it started reformatting the partitions which I then aborted but can't honestly remember as it was a month ago.

However, I will have a go with a slow burnt disk and let you know.

Cheers,
Spaaarkz. 

P.S It will have wait until tomorrow as it is late now.

---

### Post by rusty4r on 2007-03-15
So you have a partition already set up on the drive? If so maybe you are correct and in that case I would try to use Gparted to reformat that partition only.

---

### Post by Spaaarkz on 2007-03-16
> **rusty4r said:**
> So you have a partition already set up on the drive? If so maybe you are correct and in that case I would try to use Gparted to reformat that partition only.

Thanks for the help it is appreciated. However, I have tried to open Gparted to reformat the partition before the installation processes (from the cd version of ubuntu) and it hangs when it tries to open. I think the problem is with gparted - the install hangs when it tries to open gparted to which is the stage I can't get passed.

Any advice?

Cheers,
Spaaarkz.

---

### Post by rusty4r on 2007-03-16
Hmm, I hate to send you in circles but I wonder if the Gparted Live CD or the System Rescue CD would do any better. Is Gparted the program that originally partitioned your drive?

There are other partitioning and formating programs that are freeware but since I'm still green behind the ears myself I don't know how to tell you to use them when you haven't got the install done yet. But I'll keep trying to help until we catch the eye of someone with the right solution for your problem.

---

