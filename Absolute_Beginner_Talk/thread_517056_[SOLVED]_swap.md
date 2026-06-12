---
title: "[SOLVED] swap"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-08-04
i just got a new harddrive (WD Caviar 750gig WEEEEE! :D ) and plan to reinstall on that.

i'm going to make separate partitions for / and /home, but i'm not sure about swap. i have a gig of ram, and have never (not once) used all of it and required any swap space. i've dug around the forums and on google for more info on swap but all i see are strong sugestions to keep it, but no real explanation as to why.

so, if i never use all my ram, why should i keep a partition for swap? whats the real harm in not having any swap space?

---

### Post by wolfen69 on 2007-08-04
i have 2 gigs of RAM, and i'm using 52mb of swap. don't ask me why, but linux likes to use a little now and then. i would recommend having at least 256mb of ram just to keep the linux gods happy.

---

### Post by heimo on 2007-08-04
> **colddayinapril said:**
> so, if i never use all my ram, why should i keep a partition for swap? whats the real harm in not having any swap space?

If you have swap available, kernel (Linux) will be able to put some of the least used stuff from RAM to disk and try to use RAM more efficiently. Sometimes it does, sometimes it doesn't. RAM is used for program code and data, and also for disk buffers, which speed up your system. So actually having a swap and using it may be sometimes better choice than not having swap. But let's not start arguing about this subject on this thread as it has happened couple thousand times already and there are good valid points for and against.

So. You have a 750GB disk. Doesn't hurt to make one 1GB - 2GB(* partition and use it as a swap and if you feel swapping is destroying your systems performance, disable it later or use swappiness kernel parameter to tweak how agressively kernel swaps. (Instructions can be found on these forums by searching.)

EDIT: *) I wouldn't go lower than 1GB and not higher than 2GB, but this is more matter of taste. 512MB will work as well. If I've understood, at least somewhere in the past Linux used swap space for hibernate or something like that, and there was some kind of suggestion for having RAM x 1,5 swap,  but on my 3GB system I'd never use 4,5GB swap as if my system is going to use that much swap, it's going to be horribly slow and something would've gone madly wrong.

---

### Post by asmoore82 on 2007-08-04
technically, not having swapspace could lead to a situation where the Linux kernel hard locks or "crashes,"
if/when this happens it cannot be called a bug nor a failure of Linux because
the blame lies solely on the person who did not create the swapspace :KS

That having been said, you could probably get away with not having the swap if you really wanted to.

---

### Post by heimo on 2007-08-04
> **asmoore82 said:**
> technically, not having swapspace could lead to a situation where the Linux kernel hard locks or "crashes,"

You're probably correct. I think it'll try to save the situation by starting to kill some processes to free memory, but I guess that could also happen if you run out of all your memory (including swap), but if you have at least some swap, you'll have this warning when you notice system starting to swap heavily and can choose yourself to kill what-ever process has gone mad (or is just using too much resources). Yes, I recommend having swap if there's no really good reason why not (like I can imagine that many embedded systems don't want to have swap / can't have swap).

---

### Post by kerry_s on 2007-08-04
wow, 750gig's and you want to be stingy about swap, give it a gig and move on to more important things.

in fact you should use a extended setup and split your setup more than root & home. the bigger the partion the longer it takes to read the slower your systems going to feel. you can do like boot, usr, lib,etc... do some more research, big partions is not always a good thing. i would make a large data partion where you can keep backups and other important stuff, that you manually mount and unmount as needed. in a linux system anything that is mounted when the crap hit's the fan can be corrupted, you want your important stuff outside of home which is always mounted.

---

### Post by HermanAB on 2007-08-04
Well, look at it this way: Linux only uses swap when it has no other choice.

Therefore, it doesn't hurt to have some and it means that the system will keep running when it is stressed by a misbehaving program, or over taxed by an active user who may be browsing the web using Firefox with 100 tabs open while compiling a kernel... :)

---

### Post by wormser on 2007-08-04
The general rule is to make the swap 1.5 to 2 times your ram.  You have the space so just double your ram.

---

### Post by colddayinapril on 2007-08-04
wow, thanks for all the replies!

I now get that swap is important, if only to please the little grimlins that live in my computer :)


so, what abuot the swappiness setting... i fiddled around with that on my old laptop. on that set up, i was using swap even when i had a large amount of free memory (or memory only being used for cash), but i never really understood how it worked.

if i where to set the swappiness to zero, i know it would basicly prevent swap from being used, but, would the system still be able to use it when it really needed it?

that is to say, if i set swappiness to zero, would it accomplish my goal of not using swap, but give linux the option to use it when it has to?

---

### Post by kerry_s on 2007-08-04
> **colddayinapril said:**
> wow, thanks for all the replies!

I now get that swap is important, if only to please the little grimlins that live in my computer :)


so, what abuot the swappiness setting... i fiddled around with that on my old laptop. on that set up, i was using swap even when i had a large amount of free memory (or memory only being used for cash), but i never really understood how it worked.

if i where to set the swappiness to zero, i know it would basicly prevent swap from being used, but, would the system still be able to use it when it really needed it?

that is to say, if i set swappiness to zero, would it accomplish my goal of not using swap, but give linux the option to use it when it has to?

yes, mine is set on 0 & i only have 256ram, it still uses swap just not right away.

---

### Post by n.aggel on 2007-08-04
> **kerry_s said:**
> wow, 750gig's and you want to be stingy about swap, give it a gig and move on to more important things.

in fact you should use a extended setup and split your setup more than root & home. the bigger the partion the longer it takes to read the slower your systems going to feel. you can do like boot, usr, lib,etc... do some more research, big partions is not always a good thing. i would make a large data partion where you can keep backups and other important stuff, that you manually mount and unmount as needed. in a linux system anything that is mounted when the crap hit's the fan can be corrupted, you want your important stuff outside of home which is always mounted.
is there any guide about all these? because i think a lot of new ubuntu users have large hdds...

---

### Post by colddayinapril on 2007-08-04
groovy.
thanks a lot guys!

---

### Post by kerry_s on 2007-08-04
> **n.aggel said:**
> is there any guide about all these? because i think a lot of new ubuntu users have large hdds...

i haven't seen no good ones, things change so fast in linux, i could be wrong about how it is now. i was always told you should keep it to a reasonable size, because even though it may not have data in it will still be checked for data, so rather than having it spend more time than necessary reading the drive, just have it only stay in the partion where the data is. it use to not matter for for home use because not many could afford large drives, but these days people are reaching terabytes in there home systems. oh god, i feel so old. :(
anyways drives are so much faster now it may not matter, back than it was the thing to do. i'm so old school. :)

---

