---
title: "Ubuntu LiveCD&gt;GParted&gt;HFS+ Journaled..."
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by rjscott2005 on 2009-08-25
Well I tried to give my post question a semi-ineligible title but I'm not sure I hit the mark. I will dive right into my question and hope that I picked the correct forum to ask it.  
I've using the Ubuntu Live CD to partition and manage my 8GB microsd card for my G1 phone with great success. I thought I would use it to investigate an issue I've been having with my 1TB Western Digital External eSATA/USB drive and my MacBook Pro. Seems there's some sort of firmware/OS/fingerpointingineverydirection issue with eSATA and OS X but that's not really important for this question. Suffice it to say that I've got 100GB of valuable data on the drive and OS X no longer 'sees' the drive. 

I ran the LiveCD on my MB Pro and the drive shows up; files and all. All accessible and all in one piece. Great, right? Next I fire up GParted and the drive is showing up as 931GB of unallocated space. Not great, right? The only option I see is to create a partition. That'll destroy my data, yes?

Is there something I can do to make the drive visible again? It was HFS+ journaled. I found some information on this forum about creating a mount point. Is that what I need to do? 

Thanks for any advice at all.

---

### Post by rjscott2005 on 2009-08-25
> **rjscott2005 said:**
> Well I tried to give my post question a semi-ineligible title but I'm not sure I hit the mark. I will dive right into my question and hope that I picked the correct forum to ask it.  
I've using the Ubuntu Live CD to partition and manage my 8GB microsd card for my G1 phone with great success. I thought I would use it to investigate an issue I've been having with my 1TB Western Digital External eSATA/USB drive and my MacBook Pro. Seems there's some sort of firmware/OS/fingerpointingineverydirection issue with eSATA and OS X but that's not really important for this question. Suffice it to say that I've got 100GB of valuable data on the drive and OS X no longer 'sees' the drive. 

I ran the LiveCD on my MB Pro and the drive shows up; files and all. All accessible and all in one piece. Great, right? Next I fire up GParted and the drive is showing up as 931GB of unallocated space. Not great, right? The only option I see is to create a partition. That'll destroy my data, yes?

Is there something I can do to make the drive visible again? It was HFS+ journaled. I found some information on this forum about creating a mount point. Is that what I need to do? 

Thanks for any advice at all.
I thought I would add an image so it may be more obvious what I'm trying to figure out.

---

### Post by peepingtom on 2009-08-26
My best advice: Don't write anything to that drive until you fix this. Do you know what the partition tables looked like before this screwup?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
^^Open Source, I used it long ago, google around for partition table repair hfs+

Best of luck, the only satisfying way of losing data is by your own error :D

---

### Post by rjscott2005 on 2009-08-26
> **peepingtom said:**
> My best advice: Don't write anything to that drive until you fix this. Do you know what the partition tables looked like before this screwup?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
^^Open Source, I used it long ago, google around for partition table repair hfs+

Best of luck, the only satisfying way of losing data is by your own error :D
Thank you for the info. I'm running TestDisk now and I'll post the results.

---

### Post by peepingtom on 2009-08-27
O

---

