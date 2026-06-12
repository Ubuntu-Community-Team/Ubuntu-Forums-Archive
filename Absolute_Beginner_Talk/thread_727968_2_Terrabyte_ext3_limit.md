---
title: "2 Terrabyte ext3 limit ?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by byenary on 2008-03-18
Disk /dev/sdb: 5249.9 GB, 5249921187840 bytes
255 heads, 63 sectors/track, 638266 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267349  2147480811   83  Linux
root@sauterne:~# mke2fs ext3 -b 2048 /dev/sdb1


Thats what I did, so i formated this 5 Terra partition, but ended up with a /dev/sdb1 wich is 2 Terra,
any work arounds available or do I need to LVM ?

---

### Post by kryth on 2008-03-18
Just partition it into 2 terra chunks.
The limit 'in theory' I think is 4.1 terra chunks, if i did my math right.

---

### Post by anaconda on 2008-03-18
> **byenary said:**
> 
root@sauterne:~# mke2fs ext3 -b 2048 /dev/sdb1


why do you insist in using -b 2048 block size?? if you increase the block size you can make bigger partitions..  

If I remember correctly you can even have 8k block size, and with that you could make 16T partitions....

EDIT: just cheked it, and 4k is the largest block size.. but a patch is available to make the blocksize even bigger.. <64k

---

### Post by insane_alien on 2008-03-18
XFS will serve you better than ext3 on that partition. 

ext3 gets a bit slow when it is working at its extremes.

---

### Post by byenary on 2008-03-18
Hmm,
And would i be able to use it as if it was an ext3, i mean can i mount it like usual and or make it smb share and all that kinda stuff... ?

THX

---

### Post by anaconda on 2008-03-18
it would work the same.. except maybe faster.. and you can make xfs (or any linux fs) a share.
(when other computers access your share your computer reads the data and offers the data to others.. so it doesn't matter which filesystem you have..)

the only thing you wouldn't be able to do is to access it DIRECTLY from windows. Something you may have been able to do if you have installed the ext3 drivers on windows...

---

### Post by bigredradio on 2008-03-18
Just out of curiosity, do you really have that much storage? If so, what cannot be segmented into different filesystems? Having everything in one really big filesystem doesn't make sense unless there is an application that requires it. (like oracle).

If this is a fileserver, can it be organized in a way so that you have smaller filesystems? That way, if you have filesystem corruption or failure, you are not losing everything. You also take a performance hit. Try to separate out files that do not change with ones that change often. I wonder how long this would take to fsck a 4+ TB filesystem. Pack a lunch.

The old saying is true, do not put all of your eggs in one basket.

[edit] reread top of post. Guess you do have that much storage. I'd really look at how you plan to utilize it.

---

### Post by byenary on 2008-03-20
Yep we need the storage, we are active in the media and need to store lots of audio and video, i installed it using just ext3 +LVM after all...

---

