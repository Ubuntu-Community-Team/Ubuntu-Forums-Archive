---
title: "HD installation"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by three-cushion on 2006-11-25
Hello: I run Ubuntu on a G4 Mac, 1gb, 0.9 GHZ, with OS 10.4.8 (Tiger)

I install from the CD Ok... Problem was to Make a permanent  install on one of my HDs.

tried to use the Partitioner in Ubuntu... but after manually describing the 2 partitions (Sys plus Swap), I repeatedly got a sys error in not reaching a file in one partition.

So, I tried again and told Ubuntu to use "Largest Contiguous Avail. Space". this worked fine .... BUT that tied up 130+ GB of space on one of my HDs. (There was that much Avail.).

So, I returned to my Trusty Tiger system and used a life-saver 3rd party Mac app; iPartition from Coriolis (UK). It allows creating, expanding, contracting Mac partitons 'on-the-fly'. AND it WILL create Linux partitons as well! But I decided to try a brute force method.
 
Then I deleted the Ubuntu installed space, retrieving the 130 GB and I made a "dummy" partiton in that space leaving about 10GB of contiguous space.

In Ubuntu I directed its partitioner to use the largest contiguous space (now 10GB) and it installed fine.

Then back to iPartition on Mac, deleted the dummy space to get my ~120GB unused space back....

I have run fine since... 
===========================================================

Probably I need to master Ubuntu's partitoning scheme.... Even when I pre-allocated with iPartition, I could not entice Ubuntu to use that space. It seems to want to be in Control of ITS partitons....But I prevailed over that with iPartition.

Thanx for listening... Suggestions welcome...

Cheers, Jim B

---

