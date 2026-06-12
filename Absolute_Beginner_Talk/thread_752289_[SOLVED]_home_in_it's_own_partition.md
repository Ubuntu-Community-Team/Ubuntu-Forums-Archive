---
title: "[SOLVED] /home in it's own partition"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-04-11
Following Psychocats:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

to make /home a partition rather than a file on the tree of /

I have a tiny bit of experience with GParted. I want to know, after the "new" /home is partitioned and the data from the "old" /home moved to it, what do I do with the approximately 40 gig of diskspace that was once the "old" /home ???

Should I leave it for future Ubuntu OSs? 

Laughingly refer to it as the space for m$ vista? (I will never, never install)

Seriously, does the space occupied by the "old" /home need doing something with?

---

### Post by Het Irv on 2008-04-11
You could tack it onto the new /home, or you could do some distro-hopping.

---

### Post by mohnkern on 2008-04-11
Sounds like the perfect space for a VM if you've got the CPU cycles :).

It's also a good place to start if you want to play with logical volumes.

---

### Post by Oldsoldier2003 on 2008-04-11
> **Mark_in_Hollywood said:**
> Following Psychocats:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

to make /home a partition rather than a file on the tree of /

I have a tiny bit of experience with GParted. I want to know, after the "new" /home is partitioned and the data from the "old" /home moved to it, what do I do with the approximately 40 gig of diskspace that was once the "old" /home ???

Should I leave it for future Ubuntu OSs? 

Laughingly refer to it as the space for m$ vista? (I will never, never install)

Seriously, does the space occupied by the "old" /home need doing something with?

Unless you repartition again the space occupied by your old home is just part of your root filesystem. so you would need to shrink the / partition if you wanted to play with this space as a partition. yeah 40GB is a nice chunk and way, way more than is needed for the root filesystem under almost all circumstances.

---

### Post by stchman on 2008-04-11
> **Mark_in_Hollywood said:**
> Following Psychocats:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

to make /home a partition rather than a file on the tree of /

I have a tiny bit of experience with GParted. I want to know, after the "new" /home is partitioned and the data from the "old" /home moved to it, what do I do with the approximately 40 gig of diskspace that was once the "old" /home ???

Should I leave it for future Ubuntu OSs? 

Laughingly refer to it as the space for m$ vista? (I will never, never install)

Seriously, does the space occupied by the "old" /home need doing something with?

I knwo the thread is [SOLVED], but you can specify a home directory in System--->Administration--->Users and there is a tab to specify a home directory.

---

