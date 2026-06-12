---
title: "Conexant audio card"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by secreus on 2008-04-08
My conexant audio card is not working. When I installed Ubuntu, it was detected, but it will not play sound through the speakers OR the headphone jacks. (I have a hp pavillion)

Thank you for your help!

---

### Post by Matthewslf on 2008-04-08
in terminal, run
```
alsamixer
```
and check what channels are available. List all of the channels here and what they are set to.

---

### Post by secreus on 2008-04-09
It says: Master, PCM, IEC958, Ext mic, and int mic. 
The card is HDA NVidia and the chip is Conexant CX20549 (Venice)

---

