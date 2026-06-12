---
title: "no display!!!"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by manuvn on 2007-07-27
i use a dell inspiron 6400 with ati radeon x1400 graphics..
the problem is that when i try to boot the comp cant initiate the x window system.. :mad:

i get the error message as 

VESA(0) : no matching modes found
screens found, but none have usable configuration..

please help me

thank you...

---

### Post by NESFreak on 2007-07-27
<ctrl>+<alt>+<f1>
login if needed.
type:```
sudo dpkg-reconfigure xserver-xorg
```follow the instructions.
btw could be some more info [here]("https://help.ubuntu.com/community/RadeonDriver")

---

