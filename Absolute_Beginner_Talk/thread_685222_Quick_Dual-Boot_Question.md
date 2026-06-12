---
title: "Quick Dual-Boot Question"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by draceena on 2008-02-02
I'm thinking of Dual Booting my XP and Ubuntu. 

Currently my XP is on a 80gig drive connected by SATA. I have 2 other physical drives connected by IDE, one is 20 gig the other is 80. 

I'm thinking I will disconnect my SATA drive and load Ubuntu on the 20 gig drive (I use the 80 for multi-media backup).

My question is, does the 20 gig drive need to be on the IDE line as master or can it be attached as Slave.

Thanks for your time. :)

---

### Post by yaknowwat on 2008-02-02
I don't think much would stop modern hard drives as being slaves with bootable abilities though you can easily change that by going in the BIOS or messing with the jumpers on the HDD.

---

### Post by logos34 on 2008-02-02
ubuntu will boot no prob from slave drive.

But chances are grub bootloader will want to go by default on the the 80 GB IDE (master)--which it will see as '(hd0)'.  You can play it safe by hitting the 'Advanced' button on the 'Ready to Install' screen (live install cd) and change to /dev/hdb

---

### Post by draceena on 2008-02-02
Awsome!

Thanks for the information and quick replies.

:popcorn:

---

