---
title: "Is it possible(silan sc92031 NIC card)?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-02-07
Hi!!!

Is it possible to use this ethernet card(Silan sc92031) in Ubuntu? It's not configured automatically.. Moreover,the patch given for this driver is not working for ubuntu.Gettin errors when I tried to run this patch.Some people say that this card can only support kernel 2.2/2.4..... Can anyone help me?

Thanks!!!

---

### Post by Sef on 2007-02-07
Read this post on [Gmane.org]("http://comments.gmane.org/gmane.org.user-groups.linux.ilugc/34230").

---

### Post by jacksondafonseca on 2007-03-01
Download 2.6 driver: [http://gurukumara.googlepages.com/sc92031-2.6.tar.gz](http://gurukumara.googlepages.com/sc92031-2.6.tar.gz)
	Follow the procedures of readme.txt until the fourth step, the line: insmod sc92031.ko 
That's over. You don't need to edit any file. Your card must be working.
A little correction: sudo insmod sc92031.ko work_mode=0x00 

> **Sef said:**
> Read this post on [Gmane.org]("http://comments.gmane.org/gmane.org.user-groups.linux.ilugc/34230").

---

