---
title: "Having trouble with Step 4 in 7.10 installation"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by sanjay135 on 2007-12-30
I just created a new partition on my windows pc hard drive to install ubuntu 7.10. This is my first time trying to install linux and I'd like to dual boot with Win XP. I used the GParted LiveCD to create a partition about 25 GB in size. When I get to Step 4 in the Ubuntu installation process, the only two options I see are to either use the whole hard drive to install or to manually configure it myself. I picked manually for the dual boot possiblity. 

So I pick the new ~25 GB partition and try to format it to ext3 and rename it "/" so that it'll be my root drive (at least that's what I think I'm supposed to do) and press forward. Then this pops up.

"File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 24026 (47959 expected); size of FATs is 94 sectors (188 expected)."

followed by

"The test of the file system with type fat16 in partition #1 of SCSI1 (0,0,0) (sda) found uncorrected errors. 
 
"If you do not go back to the partitioning menu and correct these errors, the partition will be used as is."

I just press cancel and undo the changes to the hard drive partition and cancel the install because I'm scared to mess something up.

Could someone please tell me what's going on and what I can do to fix it and get a XP/Ubuntu dual boot? (And I really don't know much technical stuff like CLI but I'm willing to try if someone would explain clearly.)

---

### Post by spiderbatdad on 2007-12-30
have you defragged your windows hd at least twice?

---

### Post by Sef on 2007-12-30
Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

