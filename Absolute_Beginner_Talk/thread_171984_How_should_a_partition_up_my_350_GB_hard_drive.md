---
title: "How should a partition up my 350 GB hard drive?"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-07
I'm running only Dapper Beta 2 on this computer and do not intend on putting windows on it ever. However, I have read that partitioning up such a large hard drive will have numerous benifits such as making it easier to back up data, and maybe even make my system faster. So, how would you partition up a 350GB hard drive?

P.S. I'm downloading the linux system rescue cd as we speak to do the partitioning.

Thanks!

---

### Post by gondilon on 2006-05-07
I would make a 1 gb swap partition and two or three partitions out of the rest of the hard drive.

---

### Post by adam.tropics on 2006-05-08
I would probably go for a swap, about 2.5 to 3 times the memory (so 512 Mb memory,go for say 1.5Gb swap), then a small (depends on how many kernels will be kept on your system)/boot partition, and then the rest to / and /home (most for home). To be absolutely honest though, the drives are getting so large, many decisions are going to be specific to what you intend to use the machine for. 

You could always just do swap and /, and seperate a large patition for just storage as if a seperate drive.  

Search around a bit there are many threads about partitioning for deeper explained advice.

---

