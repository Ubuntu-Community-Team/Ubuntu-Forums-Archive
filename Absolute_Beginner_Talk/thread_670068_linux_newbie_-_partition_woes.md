---
title: "linux newbie - partition woes"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Ronaldp113070 on 2008-01-17
ill try to partition the entire disk manually just for ubuntu linux..... what's the ideal partition.... i want a 5Gb swap and the rest for "/" and /home... how do i do that

---

### Post by wieman01 on 2008-01-17
When you run the Live CD, you are given the option to configure your partitions manually. Then simply set up whatever partitions you like.

I recommend that you have...

1. SWAP = Size of your RAM (no more, no less).
2. /home = Let's say 10 GB, but that's really up to you.
3. / = Whatever remains.

If you have further question, just shoot! :-)

---

### Post by Sef on 2008-01-17
> ill try to partition the entire disk manually just for ubuntu linux..... what's the ideal partition.... i want a 5Gb swap and the rest for "/" and /home... how do i do that

Swap should be 1 1/2 times your memory.  However if you have 1 gb ram or more, I would not make it more than 1 gb swap.  If 2 or more, then swap is not really needed.  

Root (/) should be 8 - 10 gb.  Home can be the rest.  

If you use the LIve CD, it can do it for you, so you don't have to do it.  If you do want to manually partition, then read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") or the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").   Both are geared toward dual booting, so just skip the steps when about making a partition for both Windows and GNU/LInux.

---

### Post by ugm6hr on 2008-01-17
This appears to be a continuation reposted as a new thread: [http://ubuntuforums.org/showthread.php?t=670035](http://ubuntuforums.org/showthread.php?t=670035)

---

