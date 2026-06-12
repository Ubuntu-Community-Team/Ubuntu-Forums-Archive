---
title: "Dual Boot Partitioning Help"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Paul133 on 2006-08-23
I'm going to install Ubuntu (from the alternate CD) and I'm wondering how I should partition my 40GB HD (15 GB used; 18 GB free). Should I just do the default or should I make a FAT32 partition as well as an Ubuntu partition an NTFS partition, and a swap partition? If so, how much should I allocate to each. I'll probabaly also be getting a very large USB external drive that I'll install in about a week. What should I do? This ( [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) ) is the tutorial I've read. I think the first option would be easier but can that be done with XP (NTFS not FAT32)?

---

### Post by orb9220 on 2006-08-24
Are you trying to dual boot with xp? Then you will have to resize the hd  down to about 17gb for xp to remain with 2gb free for it's pagefile and breathing room. Which will give you 16 gb left of unallocated space. then create a 15 gb / and 1gb of swap and you should be fine.

---

### Post by professor_chaos on 2006-08-24
Dapper default takes just under 3GB. So depending on how much you will be using ubuntu vs XP, you should allocate at least 6GB for the install. Memory is so cheap these days, swap is rarely used. Considering the little amount of free space you have I would recommend just 500mb for swap.

And a small fat32 partition would be a great place to store shared read/write location for both OS's. Only you can decide how big to make this.

---

### Post by Paul133 on 2006-08-24
So, (combining your answers) I should try 17GB NTFS, .5 GB Swap, 6GB Ubuntu, and the rest (roughly 10GB) FAT32?

---

### Post by orb9220 on 2006-08-24
Sounds good and the good is the 10g fat can be accessed by ubuntu or xp.

---

### Post by Paul133 on 2006-08-25
Now the next problem I'm having is that there's some Fat16 partition around 16 MB that Dell added and there's some vague problem with it, like Windows won't recognize the file sizes of the partition or something. What do you think I should do? Just ignore it?

---

