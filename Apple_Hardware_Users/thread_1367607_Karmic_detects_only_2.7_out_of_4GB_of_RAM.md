---
title: "Karmic detects only 2.7 out of 4GB of RAM"
date: 2009-12-29
forum: Apple Hardware Users
---

### Post by gfern on 2009-12-29
Hi Everyone! 

I have a macbook 5.1 with 4GB ram (upgraded) and an installation Ubuntu Karmic. I recently noticed that both the "system monitor" tool and the "free -m" command shows only 2.7GB. MAC OS, on the other hand, is showing 4GB. Why isn't Ubuntu detecting all the memory? Is there a way to fix that? Oh yeah, this is a 32bit installation. 

Any help appreciated.

---

### Post by dennis123123 on 2009-12-30
> **gfern said:**
> Oh yeah, this is a 32bit installation.

There is your answer.

---

### Post by abel_bcn on 2009-12-30
So you're saying that for Karmic to detect those 4 gigs it must be 64bit? That doesn't make much sense does it?

---

### Post by dennis123123 on 2009-12-30
Of course it does. Theres billions of topics about RAM limits with 32 bit OSes. first one from a google: [http://community.livejournal.com/linux/1754389.html](http://community.livejournal.com/linux/1754389.html)

2.7G comes from 3.2G (approx) minus the 0.5G for graphics.

---

### Post by cobbaut on 2010-06-03
This is ridiculous, any Intel Pentium cpu has 36 bits to address memory. I have used and seen many 32bit OS'ses using the full 4GB!

Recompile your kernel with CONFIG_HIGHMEM64G=y to get 4GB. Or get Ubuntu server on your system, that also detects 4GB.

paul

---

### Post by sha.goyjo on 2010-06-03
Okay, look, you can run a 32-bit OS with PAE (physical address extensions) which will allow it to address over 3.2gb. Does that help solve your confusions? It is possible, it's just that without the extensions it's not possible. You should be able to choose the pae kernel during install

---

### Post by PRC09 on 2010-06-03
This should help....


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by eipxen on 2010-06-03
If you have a macbook pro 5,1 I believe you should be able to run the 64-bit version of Ubuntu.  Mac OSX snow leopard and leopard are both at least in part 64-bit I believe, so that is why they can see the rest of your memory.

---

