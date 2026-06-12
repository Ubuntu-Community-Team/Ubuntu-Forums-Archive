---
title: "How to partition my HD to put all my music in a new partition"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-09-30
What type of filesystem do i have to use to put all my music on and be readable from both win xp and ubuntu... i will have to resize my ubuntu partition for this

---

### Post by mindtrick on 2007-09-30
Fat32 is good for this.

---

### Post by kellemes on 2007-09-30
ext3 is better.. there are excellent ext3-drivers for Windows.

---

### Post by fasoulas on 2007-09-30
i want to resize resize my ext3 ubuntu partition that is 120 gb in size and use 20 gb for the fat32 partition..can i do this with gparted???

---

### Post by fasoulas on 2007-09-30
> **kellemes said:**
> ext3 is better.. there are excellent ext3-drivers for Windows.


Could u recommend some??

---

### Post by mindtrick on 2007-09-30
> **fasoulas said:**
> Could u recommend some??

I use Linux Reader in Windows. It can only read and I found it too slow for copying files. I've also read that writing ext3 from Windows can be risky and may result in failure. Fat32 should be less problematic and stable. 

You should be able to resize and create new partitions easily with Gparted's graphical user interface.

---

### Post by dptxp on 2007-09-30
Resize with GParted.
EXT3 is great but with FAT32 you need not use any extra drivers. Use FAT32.

---

### Post by tomot on 2007-09-30
allow me to provide you with some of my recently acquired Ubuntu install:

I have 2 dedicated HDD's both were formatted NTSF under XP. They contain only data,
such as AVI's, MOV.s, MP3's. I can play all of that stuff in Ubuntu or XP 
depending on which operating system I dual boot. 

Ubuntu is ........"FANTASTIC"....... cheers!

---

### Post by fasoulas on 2007-09-30
ok i resized my ubuntu partition and formated to fat32 using the ubuntu live cd but i need to have root permissions to access the partition(i haven't tested it on windows) how can i change the permissions?

---

