---
title: "Edgy Partitions"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by daxLeet on 2006-10-28
I want to install Edgy Eft as a secondary partition.  Three partitions already came on my PC, and I need two more for a swap and an ubuntu partition.  How would I go about making an extended partition?



I'm retarded so I need a detailed response [lol]

---

### Post by kidders on 2006-10-28
Hi there,

When creating a partition, select "Extended" as the partition type.

---

### Post by daxLeet on 2006-10-28
So I have 3 partitions I take some space from windows, make a new one, except put 'Extended' instead?  Then after that I just make another extended one of more allocated space for the swap?

---

### Post by kidders on 2006-10-28
> **daxLeet said:**
> So I have 3 partitions I take some space from windows, make a new one, except put 'Extended' instead?  Then after that I just make another extended one of more allocated space for the swap?

You won't be able to create more than one extended partition ... Bill Gates has decreed that people should only ever need 4 primary disk partitions ](*,) You can make pretty much as many as you like inside a singe extended one though ... just be careful the "parent" partition is big enough.

---

### Post by daxLeet on 2006-10-28
Ok thanks.  So use the ubuntu partition as the PARENT, then make a swap as the extended?

---

### Post by kidders on 2006-10-28
Hey again,

You've lost me a little bit. The way I see things is that you already have 3 primary partitions, so naturally you want your fourth to be an extended one. I hope I have that right.

Once you've created your extended partition, you can put as many logical partitions in it as you like, provided the extended partition is big enough for them. That's where your Edgy goes.

---

### Post by daxLeet on 2006-10-28
Ohhh.  Sorry, I misunderstood the extended partition concept.  I get it now.  Thanks brah.

---

