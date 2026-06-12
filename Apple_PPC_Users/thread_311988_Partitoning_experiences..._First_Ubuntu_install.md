---
title: "Partitoning experiences... First Ubuntu install"
date: 2006-12-03
forum: Apple PPC Users
---

### Post by three-cushion on 2006-12-03
Hello:
About 1 week ago I installed Dapper (v 6.06 LTS) on my Mac  .. I just saw this Mac-oriented forum so I decided to post this first, then follow with a post I made today in another thread...
================================================

Hello: I run Ubuntu on a G4 Mac, 1gb, 0.8 GHZ, with OS I 10.4.8 (Tiger)

I install from the CD Ok... Problem was to Make a permanent install on one of my internal HDs.

I tried to use the Partitioner in Ubuntu... but after manually describing the 2 partitions (Sys plus Swap), I repeatedly got a sys error in not reaching a file in one partition.

So, I tried again and told Ubuntu to use "Largest Contiguous Avail. Space". this worked fine .... BUT that tied up 130+ GB of space on one of my HDs. (There was that much Avail.).

So, I returned to my Trusty Tiger system and used a life-saver 3rd party Mac app; iPartition from Coriolis (UK). It allows creating, expanding, contracting Mac partitons 'on-the-fly'. AND it WILL create Linux partitons as well! But I decided to try a brute force method.

Then I deleted the Ubuntu installed space, retrieving the 130 GB and I made a "dummy" partiton in that space leaving about 10GB of contiguous space.

In Ubuntu I directed its partitioner to use the largest contiguous space (now 10GB) and it installed fine.

Then back to iPartition on Mac, deleted the dummy space to get my ~120GB unused space back....

I have run fine since...
==================================================

Probably I need to master Ubuntu's partitoning scheme.... Even when I pre-allocated with iPartition, I could not entice Ubuntu to use that space. It seems to want to be in Control of ITS partitons....But I prevailed over that with iPartition.

Thanx for listening... Suggestions welcome...

Cheers, Jim B

---

### Post by matt_risi on 2006-12-05
Thanks alot for this guide, I've been trying to figure out how to get my older brother's 17" g4 powerbook to partition so he can run edgy on the side, but it's a huge pain in the ***. iPartition it is.

---

### Post by rapid_1 on 2006-12-05
I had to just give Ubuntu one of my hd's for it to install - otherwise it would either hang if I gave it 'use available free space' or stop at 'Prepare mount points' if I went manual. PITA on the install.

---

### Post by three-cushion on 2006-12-07
See new thread posted today... Change of subject

---

### Post by stream303 on 2006-12-07
While I like iPartition, I've had success shrinking hfs+ partitions with parted.  Followed this thread and it worked great:

[http://www.ubuntuforums.org/showthread.php?t=89960&highlight=parted](http://www.ubuntuforums.org/showthread.php?t=89960&highlight=parted)

Just take it easy since parted can shrink the partitions, but can't grow them if you take it too far. :)

---

