---
title: "Is This Partition Scheme Sufficient?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by palcal on 2007-03-06
Hey, I'm hoping someone can help me adjust my partition scheme, which is currently (Ubuntu isn't yet installed):

```
/boot          50MB
/                16GB
/home        24GB
/swap         2GB
/user/local  24GB
/tmp           1GB
/var            1GB
```

sda1 and sda2 are taken up by a Windows and a Windows recovery partition, respectively. Can my partitions be better? I'm going to be using Ubuntu as a desktop OS; DVDs, music, work, programming, etc.

Thanks :)

---

### Post by taurus on 2007-03-06
There is not a whole lot of stuff in /usr/local so you may want to change that to /usr because that where most stuff will be installed, /usr/bin, /usr/lib, /usr/share, /use/man, /use/sbin, etc.

---

### Post by zekopeko on 2007-03-06
why don't you keep it simple?

swap - 1GB
/ - 15 GB (boot, usr, var ,tmp fall under that)
/home - the rest

i have 12GB root , 35GB home and 0.5 GB swap.
this is more then enough. i have a lot of programs installed on root and it's only half used.

---

### Post by ckempo on 2007-03-06
> **zekopeko said:**
> why don't you keep it simple?

swap - 1GB
/ - 15 GB (boot, usr, var ,tmp fall under that)
/home - the rest

i have 12GB root , 35GB home and 0.5 GB swap.
this is more then enough. i have a lot of programs installed on root and it's only half used.

Similar setup here, works well if you only define a / (root) and /home partition, alongside your swap space.  Have been using a setup similar to this for ages now, no point making things more difficult than they need to be.

---

### Post by rsambuca on 2007-03-06
Wow, I can't imagine why you would need all of those directories on separate partitions.  I agree with the last couple of posters - separate root, swap, and home.  Also keep in mind that you can only have 4 primary partitions on one drive so you will have to create an extended partition containing multiple logical partitions.

---

### Post by palcal on 2007-03-06
I have that many partitions because that's what people have told me to do, including Ubuntu documentation. Perhaps harder to maintain, but much easier to upgrade/recover if anything goes wrong.

---

### Post by dannyboy79 on 2007-03-06
correct, when I first wanted to use linux I read in more than 1 place to create a /boot, /, /home, /tmp, /usr, /swap, /var,  and there like a total of 10 partitions for 1 distro? You may want to make the /tmp folder a little bigger as some programs use this as their default for writing large files to it but then they get deleted. also, some printers write their sppol files somewhere, not sure if it's on /tmp. If you will be doing any video editing, then probably unless you remember to change the default location that temp files get written to. I  did this setup just like you the first time a year ago (that's when I was introduced to linux and it was Ubuntu Breezy but I waited for Dapper) but then when my hard drive failed (fricken maxtor's), i had a hell of a time backing up each partition using part image and then making sure I matched the new scheme and the partition table had to be the same etc etc on my new drive and it was a mess! SO, I guess I am saying that it does state in many places to have seperate partitions for many directories,  for a home user (not a sophisticated server), just having /boot, /swap, /root, and /home should be good enough. That's what my setup looks like. NOTE: if you do it this way, then even though you don't need an extended partition, create it now and put /home there, this way if you ever want to create more partitions, you'll have an easier time with gparted shrinking the extended partition and making a new 1 instead of having to shrink a primary partition, then make an extended partition etc etc. The main reason for having a boot partition was because in the old days you couldn't boot anything that was past the 1024 cylinder but I don't think that matters anymore with todays technology.  good luck with whatever you decide.

---

### Post by palcal on 2007-03-06
Thanks, guys. Is there any significant difference between having less directories on separate partitions vs more separate directories? It would be nice to know all the advantages/disadvantages. I'll probably have a simpler partition scheme like you suggested--for now at least :) 

How does this sound?

```
/boot  50MB
/         20GB
/swap  2GB
/home 46GB
```

I could probably unallocate more space from my Windows partition which takes over 400GB.

---

### Post by dannyboy79 on 2007-03-06
don't forget about my suggestion.

so you would have 

/boot = 50mb as primary 1
/swap = 2gb as primary 2
/ = 20gb primary 3
extended partitioning acts as partition 4 (i think this is how it does it-please correct me if I am wrong)
/home = 46gb as extended partition 5

this should be fine. i mean, you'll always get different suggestion. if you want to know advantages of having eash mount point it's own partition see here: [http://www.hccfl.edu/pollock/AUnix1/Partitioning.htm](http://www.hccfl.edu/pollock/AUnix1/Partitioning.htm)

---

### Post by palcal on 2007-03-06
Thanks a lot :) I'll go with that scheme.

---

### Post by TheMono on 2007-03-06
Before you do, change the order of it... Put swap at the end of the drive in the extended partition with /home...

---

### Post by palcal on 2007-03-06
> **TheMono said:**
> Before you do, change the order of it... Put swap at the end of the drive in the extended partition with /home...

Oh, right, OK. Why should I put swap at the end?

Do you mean:
/boot
/
/home
/swap

---

### Post by dannyboy79 on 2007-03-07
well according to the wiki for virtual memory ([http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)) you would want the swap parititon in the middle of the disk, hence why I put what I did. Although with today's hardware it may not be as critical I have still stuck to this logic. Here's the snipit from the wiki:

"Also, by using a separate swap partition, it can be guaranteed that the swap region is at the fastest location of the disk, generally the center cylinders between the inner and outer edges of the disk (except for disks with fixed heads). However with the 2.6 Linux kernel swap files are just as fast as swap partitions, this recommendation doesn't apply much to current Linux systems and the flexibility of swap files can outweigh those of partitions. And since modern high capacity hard drives can remap physical sectors you're not even guaranteed that a partition is contiguous, and even if it were, having the swap data near the rest of your data will reduce seek times when swapping was needed, so the performance claims in the earlier paragraphs probably do not apply to modern Linux systems."

And then another great piece of info relating to the swap partition and root ([http://cnlart.web.cern.ch/cnlart/236/disk_partition.html](http://cnlart.web.cern.ch/cnlart/236/disk_partition.html))
Heres the snipit from there:
"First of all, the Linux swap partition is located at the end of the disk, far from the Linux root partition. It turns out that disk heads move back and forth between them all the time, decreasing system performance. It is much better to place the swap partition as close as possible to the partition where the OS is installed."

So you do what you like I just want to make sure you make an "informed" decision not just based on what some1 tells you but based on documented info. Now of course a wiki is not a guarentee to be accurate as just about anyone can edit it but the last article I posted has a source at the bottom and it states, "European Laboratory for Particle Physics" so I would tend to lean a little towards believing that. good luck

---

### Post by palcal on 2007-03-07
Interesting stuff, dannyboy79. I apologize to you for not making the effort to find out any information myself.

Is there much difference between:
/boot
/
/swap
/home

and:
/boot
/swap
/
/home

Wouldn't the first have a slight performance increase due to the swap being between / and /home, reducing the seek times? Or am I mistaken?

---

### Post by dannyboy79 on 2007-03-07
well I am not really that knowledgable about it besides what I have read but based on what it states, then yes but I normally you don't install programs within /home and I am not sure what on your home drive would need to access the swap for memory usage. It couldn't hurt though. It's a great idea in theory!

---

### Post by rsambuca on 2007-03-07
How much RAM do you have?  I have 1Gig with a swap of 2Gigs, but I don't think I have ever touched the swap yet - so it could be a moot point if you have 1Gig or more.

---

### Post by palcal on 2007-03-07
I have 2GB of RAM

---

### Post by rsambuca on 2007-03-07
Then I think this is definitely a moot point.  Unless you are doing some heavy video editing, I'll bet you never touch your swap.

---

