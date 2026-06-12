---
title: "nVidia upgrade."
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Jimit87 on 2006-09-12
ok so i have old nVidia driver installed on my comp. but when i play a game on Linux i get really bad arti. it doesn't happend with windows. 

I have nVidia MX 420 

btw, from 

Linux IA32
Latest Version: 1.0-8774
Latest Legacy GPU version: 1.0-7184, 

which one shold i install? 

give me step by step instuction on how to upgrade my driver.

Thank you.

---

### Post by orb9220 on 2006-09-12
mx 420 I believe is a legacy card which means older card or legacy drivers.

---

### Post by Jimit87 on 2006-09-12
by that do you mean, 1.0.8774? or something else?

---

### Post by orb9220 on 2006-09-12
Latest Legacy GPU version: 1.0-7184
If that is for your card.

---

### Post by Jimit87 on 2006-09-12
can u or anyone tell me if that one will work on my GPU? i would really appreciate your help.

Thank you.

---

### Post by Jimit87 on 2006-09-13
anyone?

thx.

---

### Post by Jimit87 on 2006-09-13
come on guys, i really need help with this.

---

### Post by skymt on 2006-09-13
I just looked it up, the default Dapper driver (8762) supports your card.

As for step-by-step instruction, I can't outdo the [wiki](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

---

### Post by Jimit87 on 2006-09-13
yeah, i have that driver installed. but now i want to update my driver. which one should i use out of the two i have posted in my 1st post in this thread?

---

### Post by skymt on 2006-09-13
Well, since 7184 would technically be a *downgrade*, go with 8774.

EDIT: Here's the [list](http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html) of supported cards.

---

### Post by CatKiller on 2006-09-14
> **Jimit87 said:**
> yeah, i have that driver installed. but now i want to update my driver. which one should i use out of the two i have posted in my 1st post in this thread?

FWIW, when your card evenually makes it into the Legacy list, you **don't** want to update the driver. The whole point of the Legacy driver is because NVidia can no longer guarantee complete compatibility across the whole of their range - newer drivers make newer cards perform better, but may break the functionality or performance of older cards. So the Legacy driver is the latest driver that will still work optimally on old cards.

For the most part, newer drivers add support for newer cards rather than improving the performance of older cards, so you don't necessarily **need** to use newer drivers unless the existing ones are performing badly.

HTH.

---

