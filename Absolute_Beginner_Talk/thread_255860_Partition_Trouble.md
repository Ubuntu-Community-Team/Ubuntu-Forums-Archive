---
title: "Partition Trouble"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by guitarmaniac on 2006-09-12
I have a 40 GB hard drive with Kubuntu Dapper Drake installed on it (I'm normally a GNOME guy but I want to see what all the KDE fuss is all about).
Anyway I have 3 partitions, partition 1: 512 MB = swap partition, partition 2: 15 GB = /home, and partiton 3: 5 GB as my root partition.
I have filled up my /home partition and would like to add the remaining empty space on my hard drive to this partition but due to it being in between two partitions ](*,) I cant expand it with a normal partitioner.
Can anyone see a way of fixing this problem?

guitarmaniac

---

### Post by bigken on 2006-09-12
try this dont know if it will work but its worth a try ;) [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by stig on 2006-09-12
> **guitarmaniac said:**
> 
I have filled up my /home partition and would like to add the remaining empty space on my hard drive to this partition but due to it being in between two partitions ](*,) I cant expand it with a normal partitioner.
Can anyone see a way of fixing this problem?

I don't know about fixing the problem but perhaps there is an idea in this thread that might help you use the space:

[http://www.ubuntuforums.org/showthread.php?t=250508](http://www.ubuntuforums.org/showthread.php?t=250508)

I posted a message for help and monktbd suggested that I could mount my second disk as a subdirectory of home, e.g. as /home/myuser/data. I wonder if you could use your space in this way? I'm only a newbie so i can't say whether it would be suitable or not - but give it a thought - and good luck!

---

