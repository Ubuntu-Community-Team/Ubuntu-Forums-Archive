---
title: "partition formation during install"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2007-08-31
Hello, I'm brand new to linux so bear with me....

I just started installing Feisty Fawn and got to the part where I have to assign partitions to the hard drive. I wanted to set it up manually.

I wanted to set aside a partition for swap memory, so I created  new partition. Under mount name I put "swap", but then the installer told me that only names with "/" prefixed to it would be allowed. Then it automatically changed my swap partition's mount name to "/home".

So after trying to look around for documentation on this and not meeting any success, I just went ahead with automatic partition formation. But I really want to know what I'm not understanding here.

Also, I read somewhere that it's recommended to make a seperate partition for "/" and "/home"? Something like that? If anybody understands what that means please enlighten me...

---

### Post by diatribe on 2007-08-31
you should have changed it to /swap, not swap.  as far as a / and /home partition, / is where your os and all other directories reside.  /home is your personal directory, think of it as your user directory under windows

---

### Post by meborc on 2007-08-31
the easiest way to go about installing and partitioning IF you have FREE SPACE on your hard drive is to choose MANUAL partitioning... then choose the FREE SPACE... and then choose AUTOMATICALLY PARTITION FREE SPACE (or something .. this will automatically set root and swap partitions!

if you have already created some linux partitions just delete them... they will now show as FREE SPACE...

and if you have 1gig or more RAM you don't really need swap anyway... swap is way too slow :)

have fun!

---

### Post by silverace99 on 2007-08-31
Yeah, the automatic partitioning of free space is what I used in the end. I have 1.75 gigs of memory so I guess swap is not an issue.

> **diatribe said:**
> you should have changed it to /swap, not swap.  as far as a / and /home partition, / is where your os and all other directories reside.  /home is your personal directory, think of it as your user directory under windows

So, is /home a subdirectory of "/"? Because the thing I was reading about was saying to make it in a separate partition, so that if I have to reinstall ubuntu I won't lose my personal settings or something like that


Thanks for your explanations both of you :)

---

### Post by meborc on 2007-08-31
> **silverace99 said:**
> Yeah, the automatic partitioning of free space is what I used in the end. I have 1.75 gigs of memory so I guess swap is not an issue.



So, is /home a subdirectory of "/"? Because the thing I was reading about was saying to make it in a separate partition, so that if I have to reinstall ubuntu I won't lose my personal settings or something like that


Thanks for your explanations both of you :)

you CAN make a different partition for your home folder and mount it to /home, but i have never used it cause i fiddle a lot with the settings and i like to have a "clean sheet" @ every reinstall... i DO have a separate partition, which i use for storing movies, music and so on... both windows and linux systems can access this partition and i can be sure that my data is not lost when either systems need reinstalling...

it is up to you :)

---

### Post by diatribe on 2007-08-31
/home, even if on a seperate partition, is still technically a subdirectory of /, located on a seperate partition.  using a seperate partiton for /home would allow you to remove the partiton for / while still having your /home directory intact.  this is handy if you ever need to reinstall bu7t want to keep your personal directory and settings

---

