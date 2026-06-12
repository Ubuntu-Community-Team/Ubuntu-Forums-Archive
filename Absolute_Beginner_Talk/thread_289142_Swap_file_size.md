---
title: "Swap file size?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Whitebread1 on 2006-10-30
I have a 133 gig partition that I need to split up into a root and a swap file partition,  what size should I make the swap file?

---

### Post by 23meg on 2006-10-30
You'll get varied answers. I tend to stick to this one:

[QUOTE=Con Kolivas]**How much swapspace should I allocate?**

Unfortunately there is not much good documentation on swapspace that is meaningful on today's hardware. As the discrepancy between ram speed and hard drive speed becomes greater each year, the old rule of 2*ramsize is just plain wrong. This was in the old days because the addr space was directly mapped into the first half of the double RAM sized swap, giving an easy translation formula; only the space >> RAM size was usuable as additional space.

Since most of your ram will be filled with cache, you don't need a huge swapspace, just enough to cope with transient periods of pressure.

The size should actually depend on the speed of your hard drive. On current drives I recommend **about 256MB** of swapspace (no matter how much ram you have). You could double it for a striped raid0 array of swapspace.[/QUOTE]

[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)

---

### Post by Kateikyoushi on 2006-10-30
Depends on what programs you run, how much ram you have and how often you reboot. I am up for 10 days and the 256MB swap got full even closing every app won't free up swap at all.

I say go for 512 or 1024 depending on your ram.

---

### Post by Whitebread1 on 2006-10-30
O wow, that small.  
Second question, I'm partitioning my space manually and I'm wondering what file system I should make the root partition.  Anyone?

---

### Post by 23meg on 2006-10-30
If you're unsure and don't have a specific reason to choose another particular one, choose EXT3.

For more in-depth information see [this]("http://en.wikipedia.org/wiki/Comparison_of_file_systems").

---

### Post by Whitebread1 on 2006-10-30
Alright, thank you.

---

### Post by Kateikyoushi on 2006-10-30
I concur, everything supports ext, even windows has driver for it.

---

### Post by Chinkostu on 2006-10-30
windows can read from EXT3 filesystems?? it might make a few things (document transfers) a bit easier, as i won't have to save it then boot into ubuntu and then move it over from the ntfs partition. and if i can get permissions (pushing it a bit, but if its possible) then i can mess around with the xconf in notepad rather than nano or vi if i break it)

as for swap sizes, i put it as a 1gig partition (1024mb, not 1000 :P )

---

### Post by lexen on 2006-10-30
Just so there is no confusion, windows cannot read EXT3 filesystems out of the box.  You need to go out and get the driver from somewhere else.

Also, I think you did the right thing using a gig for the swap size.  If the hard drive is big enough I always aim for that size.

---

### Post by 23meg on 2006-10-30
You can access your EXT3 partition from Windows with [this]("http://fs-driver.org").

---

### Post by jay019 on 2008-07-18
> **Kateikyoushi said:**
> Depends on what programs you run, how much ram you have and how often you reboot. I am up for 10 days and the 256MB swap got full even closing every app won't free up swap at all.

I say go for 512 or 1024 depending on your ram.

My swap is obviously too small as every few days my laptop wont hibernate. The message, swswap - not enough free swap leads me to believe that RAM X 2 is actually a good idea. My Ram is 1500MB and Swap is only 815Mb

---

### Post by TSJason on 2008-07-18
> **jay019 said:**
> My swap is obviously too small as every few days my laptop wont hibernate. The message, swswap - not enough free swap leads me to believe that RAM X 2 is actually a good idea. My Ram is 1500MB and Swap is only 815Mb

I see your logic and I raise you one:

I make the swap partition 2X the size of the physical ram that CAN BE SUPPORTED by my motherboard. So even if I upgrade to the max I'm never over that 50%

For a reality check I think about what a particular machine may be doing - for instance some server hardware can support upwards of 16Gb or more and having 32Gb of swap - while seemingly excessive may be necessary if the machine is going to be hosting extremely memory hungry software for big websites (php, ruby on rails, fastcgi, etc, etc) then chances are the drives are going to be more than large enough now that this will only be a drop in the bucket. The thought process being "if I can prevent an issue in the future with something so ridiculous as a lack of swap space then by all means do it".

---

