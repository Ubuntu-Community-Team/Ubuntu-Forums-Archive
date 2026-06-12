---
title: "what partitions do i need"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by 565Customz on 2008-01-23
ok so once i get teh windows resized what partitions do i need to create in the free space.i have 30 gigs left to install ubuntu os and would prefer a 2 gig swap...(someone told me it worked better than smaller one..? ) i know / and /swap but i thought there was more..

if thats it, then make a 28 gig / partition and 2 gig /swap?

---

### Post by tojge on 2008-01-23
Essentially, yes, that is all you need, though you might consider creating a separate /home partition (if it's a home workstation), or /var partition in case it's a server...

---

### Post by aysiu on 2008-01-23
Read this guide to partition planning:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by 565Customz on 2008-01-23
how big would the home need to be...and what is its purpose

---

### Post by tojge on 2008-01-23
Well, there are no rules, obviously, I try to make it as large as possible. I've managed with a ~10GB / (root) partition, though if you know you'll need more, make it bigger. Generally, /home always tends to be the bigger one.

Purpose? Well, it holds all of your personal files (documents, music, videos, pics, you name it...), and should something go wrong, so you need to reinstall, or you just want to perform a clean install every 6 months, you can leave your /home untouched, and have all of your files exactly as they were

---

### Post by 565Customz on 2008-01-23
SWEEt lol. ok im gonna do 13 13 and 2 i have 28 gigs  availible.

---

### Post by 565Customz on 2008-01-23
one more ? when i resize the ntfs i need to convert all the free space to fat 32 right? fat 32 is what ubuntu works in correct?  sorry im very new to this

---

### Post by tojge on 2008-01-23
Well, no. Free space will be formatted using reiserfs (or ext3 fs), if used to install (K)Ubuntu

---

### Post by 565Customz on 2008-01-23
thanks very much good to go now here is my plan

windows         20gb
 shared fat32 10 gigs (for security)
home              10
root                14
saw                 2 and the change....for a total of 56 which is what i have

---

### Post by tojge on 2008-01-23
I'd probably go for the 14 gig /home and 10 gig /, but the difference is not that great, so, cool... :-)

Anyway, I should probably mention at this point that, as of (K)Ubuntu 7.10, ntfs-3g is enabled by default, so if you want to have a shared Win/Linux storage partition (which I presume is the intended purpose of your fat32 10 gig one), you might as well go with the NTFS one, because FAT is no longer the prerequisite to having write access for Win-filesystem-formatted partitions

---

### Post by yaknowwat on 2008-01-23
you probably will not need a 2 gigabyte swap with linux.

I've never went over 1 GiB of memory even when virtualizing a stripped down Win XP with 384 MB of ram to it.

I have 1.5GiB available (512MB shared to On-Board Graphics)

Right now my memory usage is around 400MiB though that might be because, i think a program i ran had a memory leak from Wine. ( normally its about 350 MiB )

I would suggest a 1 GiB swap as you wont really use it unless you have less than 512MB.

also from the looks of it.

Windows 20G
Linux Main 15G
Home 10G
Logical 11G
-FAT32 10G
-swap 1G

should do nicely.

---

### Post by 565Customz on 2008-01-23
> **tojge said:**
> I'd probably go for the 14 gig /home and 10 gig /, but the difference is not that great, so, cool... :-)

Anyway, I should probably mention at this point that, as of (K)Ubuntu 7.10, ntfs-3g is enabled by default, so if you want to have a shared Win/Linux storage partition (which I presume is the intended purpose of your fat32 10 gig one), you might as well go with the NTFS one, because FAT is no longer the prerequisite to having write access for Win-filesystem-formatted partitions

i got so excited i partitioned before i read this lol. so what i should do is go back and change /shared to ntfs. correct....also should i have put any space between the partitions?

i shrank windows, created extedned partition, created shared, home,root, and swap. however the only one i allowed for space around was  the root partition. 16mb in front and back. or does it not really matter?

installation successful by the way its working great! (so far) :)

---

