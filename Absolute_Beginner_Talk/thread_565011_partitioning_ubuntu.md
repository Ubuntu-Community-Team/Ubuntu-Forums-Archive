---
title: "partitioning ubuntu"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by noob_1 on 2007-10-01
hello. i just installed ubuntu completely over my existing windows setup and am interested in installing another os(thinking of minix), but i can't seem to be able to partition my current ubuntu setup.

---

### Post by Pumalite on 2007-10-01
Use Gparted:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), and 'resize' the Ubuntu partition.

---

### Post by tdrusk on 2007-10-01
use the ubuntu live cd and open a terminal. Run 
```
gparted
```

You can't do it when you are using the disk. That's why a live cd is necessary.

---

### Post by Pumalite on 2007-10-01
The stand alone, burn to CD, boot from, program is newer, more powerful and more flexible. Besides, it DOES NOT mount the partition, which is what you need.

---

### Post by tdrusk on 2007-10-01
> **Pumalite said:**
> The stand alone, burn to CD, boot from, program is newer, more powerful and more flexible. Besides, it DOES NOT mount the partition, which is what you need.

I didn't know Ubuntu Live CD mounted the partition. Good call. I was trying to save him a download. 

So threadstarter, do what pumalite says.

---

