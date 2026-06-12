---
title: "How much should I allocate for the swap file?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by youtin on 2008-02-25
When I was installing Ubuntu Gutsy, I read that I should allocate a space of 1.5 to 2 times the RAM. If I followed this, I thought that size of the swap file could be a little ridiculous for my system which has 2GB of RAM. But since I wasn't sure, I played it safe and allocated 3.4GB.  Don't you think this is a bit overkill? What's the swap file  for, anyway? Is it OK to decrease the size of the swap file to around 2GB or less?

---

### Post by LeAstrale on 2008-02-25
AFAIK linux uses the swap file mostly when you hibernate/standby by writing all the states and so on to the swap... personally i have never neede more than 1gib swap space.

---

### Post by RJ Hythloday on 2008-02-25
If you're going to have hybernate then swap should be at least equal to ram.

---

### Post by oedha on 2008-02-25
you can allocate 512mb - 1gb for swap

---

### Post by jeffus_il on 2008-02-25
If you like you can add the process monitor to your panel and watch your swap usage, you could say allocate double the maximum to your swap space just to be on the safe side.

On the other hand this could be flawed, since my usage is zero, so 2 x 0 is ?
I suppose that I could use a swap file instead, my usage is so low, and not bother about the partition, but I guess the price to pay for one Gb of a 160Gb disk is not much these days, so I guess I'll leave the 1 Gb swap partition.

---

### Post by housam on 2008-02-25
2 Gb is ok for the swap. read about it [[COLOR="Red"]here[/COLOR]]("http://www.linux.com/base/ldp/howto/Partition/partition-types.html#swap-partitions").

---

### Post by thisiam on 2008-02-25
i use 1024mb for swap but never use it, my computer never goes into standby mode so i don't need to worry about that. i guess if i didn't have a swap file it probably wouldn't go into standby mode right ?

---

### Post by Guitaraholic on 2008-02-25
hmmm i only allocated 512 to my swap file 

i never put my pc in standy thou tbh. Should this matter to me then?

ive got 4gig ram so dont fancy making an 8 gig swap file!

sound like a bit of a waste of space to me!

---

### Post by Trail on 2008-02-25
I almost never use swapping :| The only times that I do (and I have in mind) is ApexDC++ through Wine and AniDB-O-Matic through Wine again. Both have to deal with large input and stuff.

Feels such a waster to allocate even a gig of ram for swapdisk... Which is totally contrary to Windows :P

---

### Post by stallieman on 2008-02-25
It should be a bit larger than the size of your RAM.

If you have 1024 MB, your swap can be about the same. Lets say 1100 MB.

[http://www.go2linux.org/swap-file-vs-swap-partition](http://www.go2linux.org/swap-file-vs-swap-partition)

---

### Post by deepclutch on 2008-02-25
Mine,I have a 300MB swap which,I feel is more than enough.no,there is no need for such huge swap spaces!at max  1.5gigs(if u want swsusp) if u dont need suspend feature,then a swap of 300MB is more than fine.
BTW,I am running a machine with 384mb ddr-I ram and a 256mb dedicated 7300gt.

---

### Post by jeffus_il on 2008-02-25
> **Trail said:**
> I almost never use swapping :| The only times that I do (and I have in mind) is ApexDC++ through Wine and AniDB-O-Matic through Wine again. Both have to deal with large input and stuff.

Feels such a waster to allocate even a gig of ram for swapdisk... Which is totally contrary to Windows :P

But in Windows in the old days, before I saw the light, I would always make the swap file a fixed size and put it in a separate partition, because the fiddling with the size was a performance hit, (in the old days when men were tough and computers were weak), and also the swap file would stick itself in the middle of the disk, and cause a headache for the defragmenter, since it wouldn't budge.

---

### Post by Trail on 2008-02-25
> **jeffus_il said:**
> But in Windows in the old days, before I saw the light, I would always make the swap file a fixed size and put it in a separate partition, because the fiddling with the size was a performance hit, (in the old days when men were tough and computers were weak), and also the swap file would stick itself in the middle of the disk, and cause a headache for the defragmenter, since it wouldn't budge.
Yes, me too :)

---

