---
title: "HDD size"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by dbp876 on 2008-04-03
Is there a size limit for HDD's. I have a western digital (SE16WD5000AAKS 500GB 7200 rpm sata 3.0Gb/s hard drive) it will not let me install on (maybe its me) but if I change to an 80 GB  maxtor IDE drive it allows me to install fine. Using Ubuntu 7.10 64 bit   New to linux any help would be great.  Thanks

---

### Post by privaterolf on 2008-04-03
I've never run into a hard drive issue.

Is the 500GB formatted?

---

### Post by dbp876 on 2008-04-03
Yes it is formatted, tried ntfs, ext2, ext3, unallocated, tried with windows xp installed (sry have to get used to linux) without xp installed. I have it installed and working fine on my daughters older pc, this just really has me stumped.  Thanks again.

---

### Post by Tatty on 2008-04-03
What happens when you try to install?  where does it go wrong?

---

### Post by dbp876 on 2008-04-03
After you choose to install Ubuntu it ends with this error message: kernel panic -not syncing: attempted to kill idle task! and then it just stops.

maybe a little about my pc will help 

Motherboard:  evga 780 sli
Processor:     intel core 2 quad kentsfeild 2.4ghz
Ram:             crucial ballistix tracer 2 (4 gigs)
video card:     XFX 8800GT (x 2 with sli bride)
cdrom:           HP DVD 1040
HDD:              WD 500GB 7200 rpm sata 3.0Gb/s

---

### Post by dbp876 on 2008-04-04
I do believe I found the problem, I removed the nvidia SLI bridge and it loaded fine! I didn't think about the fact I removed it to install on the 80 gb HD. Hope this helps somebody else.

---

### Post by tamoneya on 2008-04-04
I have a 500GB harddrive on which i installed hardy.  It shouldnt be a problem.

---

