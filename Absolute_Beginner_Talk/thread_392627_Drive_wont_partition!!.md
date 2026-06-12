---
title: "Drive wont partition!!"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-03-24
I want to install Ububntu on my laptop as Windows XP is going weird and annoying me but Im still going to keep it so I put my live disc in and went to the partitioner and it wouldnt let me make a new one.

Why wont it work and how can I make one?

---

### Post by taurus on 2007-03-24
Perhaps you need to defrag the harddrive in XP a few times first.

---

### Post by SamTyson92 on 2007-03-24
> **taurus said:**
> Perhaps you need to defrag the harddrive in XP a few times first.

Well I defrag every day.

---

### Post by taurus on 2007-03-24
What is the error message when you try to use gparted to resize your harddrive?

---

### Post by mikewhatever on 2007-03-24
> **SamTyson92 said:**
> I want to install Ububntu on my laptop as Windows XP is going weird and annoying me but Im still going to keep it so I put my live disc in and went to the partitioner and it wouldnt let me make a new one.

Why wont it work and how can I make one?

You do know you have resize your existing Windows or another partition to make space for Ubuntu partitions, right?

---

### Post by SamTyson92 on 2007-03-24
Im not sure I will have to look.

---

### Post by mikewhatever on 2007-03-24
To create any new partition, you need unallocated space on the HDD. Free space inside a given partition is not enough. If there is no unallocated space, one of the existing partitions must be resized/shrank.

---

### Post by SamTyson92 on 2007-03-24
I found that I can re-size one so Ill do that but how much space minimum do I need to set fo ubuntu 6.10?

Please give an easy step by step guide.

---

### Post by taurus on 2007-03-24
Maybe this would give you some ideas.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by mikewhatever on 2007-03-24
> **SamTyson92 said:**
> I found that I can re-size one so Ill do that but how much space minimum do I need to set fo ubuntu 6.10?

Please give an easy step by step guide.

You'll need at least 3 BG for both swap and root, but expect it to be really tight. Somewhere around 10 GB would be a lot nicer.

---

### Post by ZeroWing on 2007-03-24
> **mikewhatever said:**
> You'll need at least 3 BG for both swap and root, but expect it to be really tight. Somewhere around 10 GB would be a lot nicer.

 I suppose that 250GB is a little much, then... :|

---

### Post by SamTyson92 on 2007-03-24
Well I want to get a portable hard drive and use that but im straped for cash so Im going to install it on my Archos Gmini 400.

---

