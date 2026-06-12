---
title: "[SOLVED] Different home partition"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2007-10-17
hey guys, what i want to do is create a seperate partition just for my Home directory. I dont have a clue where to even start on this im guessing you will have to partition it through a live cd.



Any help would be great.

Thanks
Saj

---

### Post by taurus on 2007-10-17
Yes, you have to partition your drive to include /, /home (if you decide to have one), and swap.  Basically, you need at least two partitions:  / & swap.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by reza81 on 2007-10-17
This is a nice thing to do when you making a fresh install. Are you planning to or do you want to move your home directory to a new partition ( make the new partition first I guess)

---

### Post by saj0577 on 2007-10-17
> **taurus said:**
> Yes, you have to partition your drive to include /, /home (if you decide to have one), and swap.  Basically, you need at least two partitions:  / & swap.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)


Thanks but then how do i tell the computer to look on partition home for the home directory and not use the home directory on the same partition as all the other files?

Saj

---

### Post by saj0577 on 2007-10-17
Right website.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Thanks
Saj

---

### Post by taurus on 2007-10-17
When you install Ubuntu, you can tell the installer where / is.  And if you have a separate home partition, /home, then just tell installer to use that partition and mount it to /home.

---

