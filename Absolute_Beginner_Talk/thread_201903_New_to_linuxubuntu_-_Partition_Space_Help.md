---
title: "New to linux/ubuntu - Partition Space Help"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by XiledWeb on 2006-06-22
I have a 40GB laptop that's only about 10 GB full so after trying ubuntu from the CD and liking it, I decided to install it for real. Everything was going great up until I got to step 5 and creating the partition. 

No matter what I set it at (anywhere between 5GB and 15GB) I get an error message telling me that there is not enough room for the installation. ](*,) 

I really want to avoid formatting and THEN partioning.

Any help would be appreciated.

---

### Post by az on 2006-06-22
[QUOTE=XiledWeb]I have a 40GB laptop that's only about 10 GB full so after trying ubuntu from the CD and liking it, I decided to install it for real. Everything was going great up until I got to step 5 and creating the partition. 

No matter what I set it at (anywhere between 5GB and 15GB) I get an error message telling me that there is not enough room for the installation. ](*,) 

I really want to avoid formatting and THEN partioning.

Any help would be appreciated.[/QUOTE]
Set it to 30.  The size you enter is the new size of the old partition and not the size of the new partition.

---

### Post by XiledWeb on 2006-06-22
Will try that - thanks! Now I feel completely inept... :D

---

### Post by fridayxiii on 2006-06-22
Don't worry - I banged my head against the wall for probably 45 minutes getting my HDD partitioned.  For me that was the hardest & most trying part of the install - everything else went swimmingly...:KS

---

### Post by Endow on 2006-06-22
Hey that reminds me : how do I partition my hard drive after ubuntu is installed?

And how can I have a partition common to windows and ubuntu?

---

### Post by XiledWeb on 2006-06-23
Well..I tried increasing the percentage and size, and I'm still getting that error message. ](*,) 

Is it worth checking the CD for errors?

---

### Post by tommcd on 2006-06-23
Try typing 50 %. That should divide your hard drive in half. Half for windows, half for ubuntu. 
Does your hard drive need to be defragmented? It is recomended that you do that first. I doubt that is the source of your problem, but it is a good thing to do in any case.

---

### Post by Apple 101 on 2006-06-23
Are you manually partitioning, or using the automatic process?  You need to give space to the swap partition, and a separate /home partition would come in useful too.

---

### Post by XiledWeb on 2006-06-23
Using the automatic process, I set it to exactly 50% - and I got a different error message. *"Failure to create partition space"*.

I did defrag before doing this.

---

