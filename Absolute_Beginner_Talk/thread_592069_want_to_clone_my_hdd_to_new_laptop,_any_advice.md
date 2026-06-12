---
title: "want to clone my hdd to new laptop, any advice?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by zombiepig on 2007-10-26
OK, here's my situation.
I've just got a brand new laptop, and I'd like to copy my existing ubuntu/win xp dual boot configuration to the new HDD. 
I'm rather new to linux, but if i had to guess i'd say i could do it by:
- installing both hdd's in a pc
- booting from the live cd
- partitioning up the new hdd how i want it
- using a command like 'dd' to copy the /home partition across to the new drive
- install ubuntu on the new drive, mounting the copied /home partition

does this sound about right? Will it matter if i install the 64bit version when my old laptop runs the 32 bit version? What dd command would i use to do the actual copy?

I honestly don't really care about the win xp partition, haven't booted into it in 3+ months and don't have any desire to :P

Any help would be greatly appreciated!! :)

---

### Post by sneezymelon on 2007-10-26
if you dont want the win xp partition, simply copy the home folder in a home partition in the new drive and install ubuntu on another partition in the new drive. After that, you just need to install your reqd softwares and your settings will be retained

---

### Post by FighterOfTheNightMan on 2007-10-26
You could use the dd command, but I wouldn't recommend it.  One misspelling could erase your hard disk and that wouldn't be fun for anyone.  

I recommend you use disk cloning software that allows you to burn it to a disc and from there you can load it on to your laptop.  Some on here may advise otherwise, but that's what I would do.  Here's a link to a page with descriptions of disk cloning software

[http://www.programurl.com/software/disk-cloning.htm](http://www.programurl.com/software/disk-cloning.htm)

Regards,

Brandon

---

### Post by HermanAB on 2007-10-26
Here you go:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)

Cheers,

Herman

---

### Post by trippinnik on 2007-10-26
I've used partimage before.  I haven't looked at the other links but it works quite well.  Partitioning programs / dd won't work very well if your new PC hasa different hard disk size though.

---

### Post by zombiepig on 2007-11-07
Ok, to finalize this thread:

I connected both laptop HDDs into a desktop PC then booted off the live cd. Then made a bunch of partitions on the new laptop hdd, and copied across the contents of the home partition from the old drive. I then reconnected the new hdd into the laptop, installed 7.10, and everything worked fine! :)

Thanks for all the advice!!

---

