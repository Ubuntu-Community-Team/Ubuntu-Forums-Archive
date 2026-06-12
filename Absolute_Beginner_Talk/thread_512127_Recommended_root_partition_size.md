---
title: "Recommended root partition size"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by cheetaux on 2007-07-28
What is a good partition size for the root (/) partition?  I have a 160 MB hard drive and I plan to separate the /home and / partitions.

Thanks

---

### Post by Bachstelze on 2007-07-28
I hope you meant 160 GiB... Give the root partition 7 GiB and you will be fine.

---

### Post by cheetaux on 2007-07-28
Oops, yes I meant 160 GB. 
(However my very first hard drive was 10MB for an Apple //e - I never did fill that one up)

---

### Post by AlexenderReez on 2007-07-28
i use 20g for gnome,kde ,looking glass...and a lot of softwares...stilll it is just take around 10 gig..compare to vista(ultimate),clean install (without any other software) take about 8 g.....:mad::mad:

---

### Post by cwmoser on 2007-07-28
I kept adding stuff to my Ubuntu OS and have moved it from a 20GB to an 80GB to a 160GB and now its sitting in a 250GB partition.  At the moment, my partition uses 105GB.  You might ask - why so big?  I have pictures and music and other data files in this partition -- along with several Virtual OS's most of which are 16GB each.  Take for instance VMware - this product by default uses /var/lib/vmware as the folder for Virtual Machines.  I would not have room with a 20GB partition and it would be difficult to manage if I had to redirect to another partition for data files.  It just seems so easy to work with one big partition.

Perhaps if you want to manage data and partitions you can fool with multiple partitions but I find it easier to just have one big partition.

Carl

---

### Post by zero244 on 2007-07-28
I have my root set for 10 gigs and 20 gigs for my home partition.
Linux and Linux software is very stingy with hard drive space compared to most of the windows stuff.
I have other fat partitions where I keep my music etc.
If your not dual booting set your home partition up with a lot of space, you might need it.
My root partition has never got bigger than 2 or 3 gigs so far.

---

### Post by Avinash.Rao on 2008-07-06
Sorry, i am opening this thread again. Is there a document that talks about the recommended partition size for root, swap, etc.. for Ubuntu 8.04?? something like a best practice. I couldn't find much information.

Thanks
Avinash

---

### Post by Sealbhach on 2008-07-06
This guide gives 5-10GB.

I use 9GB for my root partition - should be enough, it's not Vista.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If you're worried about needing space for later versions of Ubuntu, make it 10GB, you will have more than enough.

.

---

### Post by forger on 2008-07-06
How about this: 
10gb for root, 1gb of swap, the rest should go to home and a backup partition :)

---

### Post by Avinash.Rao on 2008-07-06
Thanks!  not very comprehensive though.

What is disk layout when you choose a automatic disk layout option during installation? 
Lets say, i have a 30GB HDD and i choose automatic or let ubuntu to partition the disk and create filesystems. What filesystems will it create and of what size?

---

### Post by forger on 2008-07-07
Why don't you try it out?
When you choose automatic and press the next button, it should show you the "layout" of the changes that it is about to do about the partition size etc

---

### Post by ali999 on 2008-07-07
I have a 200gb drive and have it only 15 gigs of it partitioned for my root....and this is probably an overkill.

---

