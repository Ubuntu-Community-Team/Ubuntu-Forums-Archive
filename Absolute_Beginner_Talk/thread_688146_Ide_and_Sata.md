---
title: "Ide and Sata"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-02-05
This is more hardware related, but hoped someone here could help. I have two ide's drives setup one as cable select the other slave, both western digital. I Ubuntu on the slave and xp on the master dual booting. Now i just added a 500gb sata, but it's not detected, is there something I need to do.

---

### Post by hhhhhx on 2008-02-05
whats it formatted into? also you might want to check your sata cables, mine go bad, or get pulled out alot.

---

### Post by anderskitson on 2008-02-05
I just bought the hardrive  today, ill make sure the cables are in for sure.

---

### Post by njparton on 2008-02-05
When you say it's not detected, where are you looking?

Is it detected in the BIOS?

Can you post the output of the following:

```
ls /dev/sd*
```

Install gparted and see if it's detected by that?

---

### Post by hyper_ch on 2008-02-05
maybe you need to set jumper to use a lower speed for the sata drive.

---

### Post by anderskitson on 2008-02-05
never mind, im so dumb, i just had to enable sata, in my bios and I can now see it in gparted and format it. 

SOLVED

---

### Post by anderskitson on 2008-02-05
thanks, this is the best forum, its becoming more and more the reason i use linux as my main os

---

### Post by anaconda on 2008-02-05
> **anderskitson said:**
> This is more hardware related, but hoped someone here could help. I have two ide's drives setup one as cable select the other slave, both western digital. I Ubuntu on the slave and xp on the master dual booting. Now i just added a 500gb sata, but it's not detected, is there something I need to do.

Öh.. "one is cable select and the other is slave"??? You should either have both to be cable select or one master and one slave.. (I personally prefer master/slave)

---

### Post by hyper_ch on 2008-02-05
I had the problem that my old computer couldn't recognize SATA II drives... I had to jumber it to slower speed and the 500gb drives works fine ever since...

---

