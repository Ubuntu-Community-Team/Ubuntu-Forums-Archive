---
title: "The demo is great But I'm having trouble Installing Ubuntu"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by KyOT on 2006-10-03
I am trying to install unbuntu, but I am having trouble.  I don't think I have enough space on my harddrive.  There is about 74 GiB total.  I have about 23GiB free.  How much space does ubuntu take up?  Install wont let me partition, it won't let me do it manually either.  It seems the only other option is to erase my disk!!!???!!!  ](*,)  That can't be a good option right?  What about all my files, and my windows?  I don't know what to do next.

I have a PC.

Any help would be appreciated.

---

### Post by jd65pl on 2006-10-03
23 gig should be plenty to install ubuntu on, could you try partitioning using [gParted live]("http://gparted.sourceforge.net/livecd.php") cd?

I would highly recommend you backup all your info first before doing any partitioning also defrag your hard drive in windows.

---

### Post by bigken on 2006-10-03
ok defrag your windows 1st the download [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD you will also need a iso burner get [this]("http://isorecorder.alexfeinman.com/isorecorder.htm")
now will be able to downsize your disc give yourself about 15 to 20 gig good luck

---

### Post by Jussi Kukkonen on 2006-10-03
> **bigken said:**
> ok defrag your windows 1st the download [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD you will also need a iso burner get [this]("http://isorecorder.alexfeinman.com/isorecorder.htm")
now will be able to downsize your disc give yourself about 15 to 20 gig good luck
Defragmentation is good advice -- without that the Windows partition can't be made smaller.  The steps you need to go through are:
1. take backups
2. defrag
3. resize the Windows partition, if it currently takes all space
4. add a linux partition (maybe two if you want a separate /home) and a swap partition (about as big as your memory)
5. Continue install

I'm not sure why you'd need the gparted liveCD though, the Dapper installer should be able to do phases 3 and 4 ...

---

### Post by bigken on 2006-10-03
point of thumb always make your swap partion twice the size of your memory ie if you have 512mb ram make your swap 1 gig :)

---

### Post by _simon_ on 2006-10-03
> **bigken said:**
> point of thumb always make your swap partion twice the size of your memory ie if you have 512mb ram make your swap 1 gig :)

ah but the more memory you have the less the swap will be used. 

I have 1Gig memory and a 500Mb swap. The most I ever saw my swap used on Dapper was about 160Mb

---

### Post by bigken on 2006-10-03
> **_simon_ said:**
> ah but the more memory you have the less the swap will be used. 

I have 1Gig memory and a 500Mb swap. The most I ever saw my swap used on Dapper was about 160Mb

better safe than sorry :-\"

---

### Post by Sef on 2006-10-03
Read this excellent tutorial to [dual boot.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by KyOT on 2006-10-03
Thanks!

---

### Post by KyOT on 2006-10-03
> **Jussi Kukkonen said:**
> Defragmentation is good advice -- without that the Windows partition can't be made smaller.  The steps you need to go through are:
1. take backups
2. defrag
3. resize the Windows partition, if it currently takes all space
4. add a linux partition (maybe two if you want a separate /home) and a swap partition (about as big as your memory)
5. Continue install

I'm not sure why you'd need the gparted liveCD though, the Dapper installer should be able to do phases 3 and 4 ...
Thanks! but how do you add a linux partition and a swap partition?


"4. add a linux partition (maybe two if you want a separate /home) and a swap partition (about as big as your memory)
5. Continue install"

---

### Post by CatKiller on 2006-10-04
Either using the Gparted cd if you downloaded that, or as part of the install. You create new partitions in the free space that you made and format one as ext3 and the other as Linux swap. Then install Ubuntu into the ext3 partition.

---

