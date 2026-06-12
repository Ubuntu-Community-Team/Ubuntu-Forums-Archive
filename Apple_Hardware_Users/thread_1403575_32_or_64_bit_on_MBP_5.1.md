---
title: "32 or 64 bit on MBP 5.1?"
date: 2010-02-10
forum: Apple Hardware Users
---

### Post by Aybara on 2010-02-10
I have installed the 32 bit version, but all of a sudden it occured to me that I could and maybe should have installed 64. Does it make much difference on this hardware?

---

### Post by sanderj on 2010-02-10
Assuming MBP means MacBook Pro, it all depends on the CPU. You need a Core 2 Duo (not a Core Duo) for 64-bit Ubuntu. Check your model here: [http://en.wikipedia.org/wiki/MacBook_Pro](http://en.wikipedia.org/wiki/MacBook_Pro)

---

### Post by Aybara on 2010-02-10
I wasn't verbose enough :)

MPB is MacBook Pro, and 5.1 means that it's a Core 2 Duo, so I know that I _can_ run 64 bit on it. My question is if the difference is so big that it's worth reinstalling since I already installed 32 bit :)

---

### Post by buntuLo on 2010-02-10
it depends on the amount of RAM you have: if you got 4 GB or more, you need the 64 bits architecture to map them all. if you got the standard 2 GB, just stay with your 32 bits install, no major differences.

---

### Post by Nikos.Alexandris on 2010-02-10
+1 for 64bit :-)

---

### Post by ichigo on 2010-02-11
> **buntuLo said:**
> it depends on the amount of RAM you have: if you got 4 GB or more, you need the 64 bits architecture to map them all. if you got the standard 2 GB, just stay with your 32 bits install, no major differences.

If it's just for the ram you don't have to reinstall ubuntu. Just look for the pae kernel version in the repositories. It allows you to address all your ram.

---

### Post by sanderj on 2010-02-11
> **ichigo said:**
> If it's just for the ram you don't have to reinstall ubuntu. Just look for the pae kernel version in the repositories. It allows you to address all your ram.

Indeed. And I hear rumors the PAE-kernel is installed by default (if use the 32-bit kernel and you have 3+ GB RAM).

So, 64-bit is not necessary for using your 3+GB RAM, but IMHO it has a higher coolness factor.

---

### Post by alexmurray on 2010-02-11
[64bit is also faster than 32bit in general]("http://www.phoronix.com/scan.php?page=article&item=616&num=1")

---

### Post by sanderj on 2010-02-11
> **alexmurray said:**
> [64bit is also faster than 32bit in general]("http://www.phoronix.com/scan.php?page=article&item=616&num=1")

Good point!

---

### Post by Aybara on 2010-02-11
It didn't choose the PAE-kernel by default, but now I have it isntalled and all is well.

Think I'll keep using it for now, and perhaps do a clean install of 64-bit 10.04.

---

