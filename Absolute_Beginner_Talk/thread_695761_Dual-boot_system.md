---
title: "Dual-boot system"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2008-02-13
I am at the moment running Windows XP, but i would like to set up a dual boot system and have a choice to load either Windows or Ubuntu when i boot up the computer. So, could someone tell me when i come to "Prepare disk space" and choose:

"Guided - resize IDE1 master, partition #1 (hda1) and use freed space".

How much of the available free space on the hard drive should i allow to be converted into a partition for use by Ubuntu?

Any help and/or advice is really appreciated. Big thanks

---

### Post by earobinson on 2008-02-13
5 Gigs will be enough for ubuntu, you can then mount the ntfs drive and save your files there for example.

(I use a 10G partition for my ubuntu install and it always has lots of space)

---

### Post by kaiju on 2008-02-13
yeah, 5 gb will surely do it.
and don't forget to make another small partition for swap.

---

### Post by oilchangeguy on 2008-02-13
> **kaiju said:**
> yeah, 5 gb will surely do it.
and don't forget to make another small partition for swap.

not needed. let ubuntu set it's own partitions. it does a fine job!

---

### Post by Sinkingships7 on 2008-02-13
if you have a big hard drive, stretch for 10 GB for the main hard drive, so you can have the full experience. 

i can't stress this enough: you must have a large swap file. an error a lot of people make is putting the minimum for the swap, then they get tons of errors. my swap is around 5 or 6 GB right now, but that's just being paranoid because i've had some bad experiences. it should be twice your ram (mine is 2 GB) as a standard.


if you really love ubuntu, you can always wipe out windows later and let ubuntu take over your hard drive. and there's always tons of people here who are willing to help if you need it.

---

### Post by oilchangeguy on 2008-02-13
> **Sinkingships7 said:**
> if you have a big hard drive, stretch for 10 GB for the main hard drive, so you can have the full experience. 

i can't stress this enough: you must have a large swap file. an error a lot of people make is putting the minimum for the swap, then they get tons of errors. my swap is around 5 or 6 GB right now, but that's just being paranoid because i've had some bad experiences. it should be twice your ram (mine is 2 GB) as a standard.


if you really love ubuntu, you can always wipe out windows later and let ubuntu take over your hard drive. and there's always tons of people here who are willing to help if you need it.

what has made you think you need that much swap space. do you understand what swap is? it's virtual ram. if the computers physical ram can't handle it, the computer will assign unused space on the hard drive as virtual ram. this is rarely needed. as most modern computers have more than enough physical ram to do what's needed. go to system monitor and see just how much swap your computer is NOT using.

---

### Post by timzak on 2008-02-13
> **Sinkingships7 said:**
> if you have a big hard drive, stretch for 10 GB for the main hard drive, so you can have the full experience. 

i can't stress this enough: you must have a large swap file. an error a lot of people make is putting the minimum for the swap, then they get tons of errors. my swap is around 5 or 6 GB right now, but that's just being paranoid because i've had some bad experiences. it should be twice your ram (mine is 2 GB) as a standard.


if you really love ubuntu, you can always wipe out windows later and let ubuntu take over your hard drive. and there's always tons of people here who are willing to help if you need it.

Here's a different perspective:  I use a 512 MB swap on a 2 GB system and I've never seen the swap size get used at all (I monitor with conky).  On a old laptop I have with 384 MB of ram, I use a 256 MB swap and I've never seen it use more than ~50 MB.  For sure I've never seen the errors you are referring to.

I guess it depends on how many programs you try to load at once.  I generally don't have more than 4 apps running at once (one per workspace).

To the original poster:  are you planning on installing Ubuntu on the same hdd as Windows, or a separate hdd?

---

### Post by kaiju on 2008-02-13
> not needed. let ubuntu set it's own partitions. it does a fine job!

oh, okay, i didn't know that.
does the install process do a calculation of how much swap is needed or how does that work?

---

### Post by Sinkingships7 on 2008-02-13
yeah, i don't know what i did back then, but all i know is i made my swap tiny ('cause i only had a 40 GB hard drive) and the whole thing crashed on me. i came here and diagnosed the problem (i think) and it lead to an insufficient swap partition; not enough room. it was a long time ago, but i just thought i'd share my experiences.

and yes, i know what the swap file is lol

---

### Post by Sinkingships7 on 2008-02-13
> **kaiju said:**
> oh, okay, i didn't know that.
does the install process do a calculation of how much swap is needed or how does that work?

yes, it calculates if for you. don't listen to my crazy stories, it really isn't that big of a deal. i've just had big problems with it in the past, and i don't want to see that happen to someone new.

---

### Post by oilchangeguy on 2008-02-13
> **kaiju said:**
> oh, okay, i didn't know that.
does the install process do a calculation of how much swap is needed or how does that work?

yep, ubuntu will set it's own partitions. no need to do all of this manual partition. to many screw ups involved. simply let the operating do what's best for it.

---

### Post by kaiju on 2008-02-13
@oscarthefish

i have 6.3 gb for my ubuntu partition, of which 4.8 gb are used, 1.8 of that being my home directory. so ubuntu only takes up around 3 gb on my machine (but then i mostly use light apps).
also, you might want to consider using a separate partition for /home. whatever you think fits your purpose best.

hope this gives you a rough idea :)

---

### Post by kaiju on 2008-02-13
> **oilchangeguy said:**
> yep, ubuntu will set it's own partitions. no need to do all of this manual partition. to many screw ups involved. simply let the operating do what's best for it.

oh in that case i apologize for my evilly misleading post.  i guess i just never got to experiencing that part since i like setting up my partitions beforehand, using gparted from the livecd :)

---

### Post by oilchangeguy on 2008-02-13
> **kaiju said:**
> oh in that case i apologize for my evilly misleading post.  i guess i just never got to experiencing that part since i like setting up my partitions beforehand, using gparted from the livecd :)

while ubuntu does give you the option to set partitions manually, the majority of computer users what to keep things as simple as possible. so for them allowing ubuntu to do it's own thing is the way to go.

---

### Post by oscarthefish on 2008-02-13
Yes sir! Oilchangeguy was spot on. I just let ubuntu do it's thing and now i have a dual booting system and everything is working just dandy.  O happy days lol. Thanks for all the replies folks. Cya

---

