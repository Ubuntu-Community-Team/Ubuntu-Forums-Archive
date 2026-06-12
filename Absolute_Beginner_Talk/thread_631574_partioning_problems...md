---
title: "partioning problems.."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by circaender on 2007-12-04
so now my C drive will not let me partition it..i tried on install and with a program..it just doesnt want to let me partion it... there is 100g left on it.. so what could be the problem?

---

### Post by khgiese on 2007-12-04
What are you using to attempt the partition change?

---

### Post by circaender on 2007-12-04
partition magic, and when i was trying to install ubuntu, it said i  couldnt partition the drive for unknown reasons...im running vista btw..

---

### Post by jrz on 2007-12-04
We just finished partitioning our drive using the gparted live CD which appears to work very nicely. It's just a little over 50MB of download in .iso format.

---

### Post by markharding557 on 2007-12-04
use the installers partition tool on the live cd and it should do just fine

---

### Post by jackpetrilli on 2007-12-04
> **circaender said:**
> partition magic, and when i was trying to install ubuntu, it said i  couldnt partition the drive for unknown reasons...im running vista btw..

My Partition Manager worked.  Let me shrink my Windows partition.  I left the new space unpartitioned.  The Ubuntu installation found the new space and auto setup its own partitions.

Will your PM allow you to shrink your Windows partition?

- Jack

---

### Post by crjackson on 2007-12-04
> **circaender said:**
> so now my C drive will not let me partition it..i tried on install and with a program..it just doesnt want to let me partion it... there is 100g left on it.. so what could be the problem?

You probably have fragmented data on the drive where you're trying to make the partition.  You need to defrag the drive several times to consolidate all the data and then do your partitioning...

---

### Post by circaender on 2007-12-04
I tried on install of Ubuntu..and it said it couldnt partition do to unknown reasons.. 
its not allowing me to partition or anything on that drive..only on my D drive..which is my windows backup im guessing because it only 5gb.

---

### Post by crjackson on 2007-12-04
> **circaender said:**
> I tried on install of Ubuntu..and it said it couldnt partition do to unknown reasons.. 
its not allowing me to partition or anything on that drive..only on my D drive..which is my windows backup im guessing because it only 5gb.

As stated above, that's usually due to a fragmented file system or even a dirty file system from an inproper shut down.  Scan the drive for errors, fix as needed, then defrag until all the free space is consolidated, this will put all the data in one place so you won't be choping it into pieces.

Once that is done, you probably will have no problems.  I've had it happen to me and seen it happen to many others...  It won't partition the drive so as to protect you from data loss.
[COLOR="Red"][U]
**EDIT:  As always, you should back-up all your data befor trying to edit a partition.**[/U][/COLOR]

---

### Post by khgiese on 2007-12-04
> **circaender said:**
> I tried on install of Ubuntu..and it said it couldnt partition do to unknown reasons.. 
its not allowing me to partition or anything on that drive..only on my D drive..which is my windows backup im guessing because it only 5gb.

As the others said try defrag on your hard drive.

Did you use Gparted from the Live CD to see/adjust the partition before trying the install?

---

### Post by jackpetrilli on 2007-12-04
> **circaender said:**
> I tried on install of Ubuntu..and it said it couldnt partition do to unknown reasons.. 
its not allowing me to partition or anything on that drive..only on my D drive..which is my windows backup im guessing because it only 5gb.

CrJackson made a good suggestion about defragmenting.  Gparted (Ubuntu partition manager) and Partition Magic are supposed to do a mini-defragment on their own but maybe they aren't in your case.  Are you using a version of Partition Magic that works under Vista (ie Version 8.0)?

- Jack

---

### Post by bigken on 2007-12-04
what amount of partitions does the drive already have ? you can only have four primary partitions if this is your issue delete one of them and create an extended 
partition

---

### Post by crjackson on 2007-12-04
circaender 

You are really hard to help.  You've gotten some good answeres here, yet you went off and made 2 new threads for the same issue.

How about you stick to your main thread to get your problems resolved?

---

