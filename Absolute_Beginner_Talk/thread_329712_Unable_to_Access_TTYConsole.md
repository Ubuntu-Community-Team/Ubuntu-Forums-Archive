---
title: "Unable to Access TTY/Console"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-01-02
I found a couple of posts pertaining to my problem but they were either ATI related or very technical (to me at least)

I run Dapper on a HP dual core intel with a 256Nvidia card

I dont know exactly when this started but all of a sudden I am unable to access my ctrl>alt>fn1,2,3,4,5,6   When I switch over I only get a black screen but I am able to switch back into X using ctrl alt f7

I have a feeling this problem has something to do with X sice the other posts dealt with it too,
and around the same time I started to see some funny orange lines during the boot sequence.

Any Ideas would be greatly appreciated

---

### Post by maxamillion on 2007-01-02
TTY sessions accessed via ctrl+alt+f[1,2,3,4,5,6] are not affected by X. If I remember correctly that is simply the VGA output or possibly frame buffer (if you have it enabled). I'm really not sure why you wouldn't be able to access them though, they are generally the "fail safe" and generally accessed when users are experiencing issues with X.

---

### Post by charles.g.moore on 2007-01-03
how would i know if i had the frame buffer enabled???
thanks in advance

---

### Post by charles.g.moore on 2007-01-11
Anybody having the same problem, any ideas on how to fix the problem?

---

### Post by asus on 2007-01-18
yeah.. dones anyone have any ideas?  i have the same issue after updating to the lastest nvidia drivers. im using dapper

---

### Post by Deliann on 2007-02-10
I only started using Ubuntu three days ago, but I was able to solve a very similar problem with the fglrx drivers, even though I've got an ATI card, I think it might apply to you as well: [take a look at this]("http://ubuntuforums.org/showthread.php?p=2133189&posted=1#post2133189").

(Hope nobody kills me for replying to a three week-old topic!)

---

