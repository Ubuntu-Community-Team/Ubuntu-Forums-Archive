---
title: "Partitioning New Installations"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Humph on 2007-10-22
I've decided to take the plunge and drop my XP partition and go for a full Ubuntu install.

What I would like to know is: what is the best disk layout?

I was thinking about:
Partition1: (4GB) Swap
Partition2: (50GB) Ubuntu
Partition3: (100GB) /home

Is there a "better" partition layout? 

Your thoughts would be much appreciated.

---

### Post by forestpixie on 2007-10-22
I'd think that 50Gb for you / partition is too big although it depends what you're intending to do, but you'll get more replies yet I'd imagine - I've got 8Gb partition with 50% free. I'd make / less and increase /home.

Also a 4Gb swap is a bit excessive - with 1.3Gb I have 1Gb swap and very rarely use more than 40Mb of swap - but it does depend on waht you'll be doing

---

### Post by Sef on 2007-10-22
> was thinking about:
Partition1: (4GB) Swap
Partition2: (50GB) Ubuntu
Partition3: (100GB) /home

Is there a "better" partition layout? 

Partition1: (10 GB) Ubuntu

Partition2: (150GB) /home

Partition3: (1GB) Swap

As has been mentioned, root and swap don't need to be so big.  Increase your home partition.  How much ram do you have, and what do you mostly do?

---

### Post by Humph on 2007-10-22
> **Sef said:**
> Partition1: (10 GB) Ubuntu

Partition2: (150GB) /home

Partition3: (1GB) Swap

As has been mentioned, root and swap don't need to be so big.  Increase your home partition.  How much ram do you have, and what do you mostly do?

Thanks for the replies so far.

My current Ubuntu installation is 18.3GB in size already, and as I only installed it last week I'm concerned that I may run out of space if I have less than 50GB.

I selected a swap size of 4GB based on my Windows experience: "Recommended swap file size" = 1.5 x Physical Ram = 2GB x 1.5 = 3GB with maximum size of 4GB. So I've always set swap file to maximum size to ensure I get a contiguous swap file. I'm not sure I've ever actually used the swap in Linux, so I guess I could reduce it to 2GB.

Most of my activity is GIMP and PHP editing. Hoping to get into some Python and/or Gambas in the future.

---

### Post by hyper_ch on 2007-10-22
I'd say 15-20 GB on the / (root) partition. Some programs make excessive use of the /tmp folder (e.g. when ripping a dvd...)

---

### Post by realvz on 2007-10-22
from my preference i use 20GB on root/
and then if i run out of space in my /home drive then i just make a folder on / and mount it inside my /home

---

### Post by forestpixie on 2007-10-22
> **hyper_ch said:**
> I'd say 15-20 GB on the / (root) partition. Some programs make excessive use of the /tmp folder (e.g. when ripping a dvd...)

something I'd never thought about as I don't do it - shall remember that pearl though :)

---

### Post by Humph on 2007-10-22
Thanks for your input folks.

I've gone for a 20GB root partition, 138GB home partition and a 2GB swap.

XP has been expurgated. Going to kind of miss not having the partition there any more.

---

### Post by hyper_ch on 2007-10-22
Why not dual-boot at first?

---

### Post by realvz on 2007-10-22
> **Humph said:**
> Thanks for your input folks.

I've gone for a 20GB root partition, 138GB home partition and a 2GB swap.

XP has been expurgated. Going to kind of miss not having the partition there any more.

Always a good idea to remove MS junk from your PC...

IMHO

---

### Post by mivo on 2007-10-22
20 GB still seems too large to me. I have installed quite a few applications on top of everything that ships with Ubuntu, and my / uses 4.4 GB of 10 GB. I could probably trim it down by 1 GB if I removed some stuff that I never use. My /home is 230 GB, with about 100 GB free ... mostly videos, audio files, and ISO images. Oh, and some Windows programs that I occasionally use, which also go into /home.

---

### Post by realvz on 2007-10-22
like i said...i mount a part of / into my home drive...so i actually use 12GB part of 20gb / into my /home

---

### Post by Humph on 2007-10-22
> **hyper_ch said:**
> Why not dual-boot at first?

I've had Ubuntu on this machine for over a year now, and I really can't see any necessity for keeping the XP partition. Everything I used to do in Windows I can now do in Linux. Maybe not as conveniently, but it's doable.

---

### Post by glotz on 2007-10-22
Welcome to the light side mate! Congrats!

---

### Post by Humph on 2007-10-22
> **glotz said:**
> Welcome to the light side mate! Congrats!

Heh. Thank you :)

Sadly I have to keep XP on my laptop to support my unenlightened clients. :(

I'd love to find a company that was willing to adopt FOSS solutions, but it is, sadly, a fantasy.

---

### Post by mivo on 2007-10-22
It is a start nonetheless. :) While I am sure it will be many years before non-MS OSes will gain a significant market share (20%+), I do not doubt that it will eventually happen.

Linux has really picked up over the past few years, and I think it really needed a flagship distro like Ubuntu. This sounds fanboy'ish, but what I mean is that average users are turned off by being confronted with 300 distros to choose from, so having one that people almost equal to being "the" Linux is quite beneficial.

It took me five years before I was finally in the position where I could ditch Windows completely (there were job matters to consider too, and a complete change only became possible this year) -- and hey, it's still a fantastic learning experience. :) Nothing wrong with having a little fun while working!

---

### Post by bliffle on 2007-10-22
I keep that ol' XP partition around to handle surprises, especially when traveling. For example, you may find yourself someplace without WiFi and have to use dialup (which you've never tried before with linux, right?) and you find that it's difficult. But with XP it's easy.

You can almost always get dialup working in XP.

---

### Post by Humph on 2007-10-22
I've only ever used dial-up on other people's machines on XP. With my LAN I'm never likely to have to see if I *can* work out how to do dial-up.

WLAN on Ubuntu does seem to be a bit flakey, especially with WEP. I'm darned if I can fathom out how to get it working in my local pub. Needless to say it works flawlessly in XP :sad: It would be very nice to have some wrappers and such around the WLAN elements in Ubuntu. Maybe when I've actually learned some more about Python, etc. I'll have a go.

---

