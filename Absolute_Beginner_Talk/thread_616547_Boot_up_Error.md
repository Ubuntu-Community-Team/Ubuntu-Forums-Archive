---
title: "Boot up Error"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by MEB202073 on 2007-11-18
It's a dell, so I posted it here.

[http://ubuntuforums.org/showthread.php?p=3794528#post3794528](http://ubuntuforums.org/showthread.php?p=3794528#post3794528)

Anyway, how do I get my 1505 inspiron to boot right?

---

### Post by mikeyphi on 2007-11-18
Could you post some more info?

Do you get a Grub option page during the boot sequence or does it boot straight into windows?

What Ubuntu OS did you (try) install? 64/32bit? Gutsy?

Do you have a LiveCD?

Can you look at your hard drive and confirm the partition settings?

---

### Post by MEB202073 on 2007-11-18
What is a grub page?

All I get is some Dell software telling me that I screwed up somewhere in the form of

Press f2 to retry, f8 for setup and f12 for diagnoses. 

So I guess it is trying to go into windows, but honestly, I don't have a clue.


I could access the partitions in Windows with disk mangment, but I don't know about ubuntu iother then using the cd 7.10 during start up.

Did the link I give help any?

---

### Post by meierfra on 2007-11-18
Boot from the LIve CD. Open a terminal (Applications ->Accessories-> Terminal)
and type


```
sudo fdisk -l 
```
(l is a lower case L, not the number one)

Copy the output and post it here.

---

### Post by meierfra on 2007-11-18
I see. You rather start new threads than answer the questions of the people how are trying to help you:

[http://ubuntuforums.org/showthread.php?t=616743]("http://ubuntuforums.org/showthread.php?t=616743")
[http://ubuntuforums.org/showthread.php?t=616742]("http://ubuntuforums.org/showthread.php?t=616742")
[http://ubuntuforums.org/showthread.php?t=616537]("http://ubuntuforums.org/showthread.php?t=616537")

---

### Post by meierfra on 2007-11-18
From your other thread  it seems that you are using wubi. Is that correct?

---

