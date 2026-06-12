---
title: "sticking a shell script"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Adaptor on 2008-01-06
If i wanted to put a shell script i wrote so that as soon as you log in, it appears, where would i go about putting that?  Thanks

---Adaptor

---

### Post by p_quarles on 2008-01-06
That depends on two things:
1) What desktop environment are you running?
2) Where do you want the script to appear?

---

### Post by Adaptor on 2008-01-06
sorry i'm really new to this. desktop environment? and just right after the logon screen

---

### Post by p_quarles on 2008-01-06
> **Adaptor said:**
> sorry i'm really new to this. desktop environment? and just right after the logon screen
Well then, this is just a guess, but I'd say you want to move the script to your desktop folder. Open a terminal, and run this:
```
mv *name-of-script-file* ~/.Desktop
```
Let us know if that works.

---

### Post by Dr Small on 2008-01-06
Are you wanting the script to run as soon as you login or appear on your desktop ?

---

### Post by Adaptor on 2008-01-06
well that may been the answer for somthing else.  Hahaha you just help me with that script with the date rember?  It was like 

echo "hello world it is now`date +%a`"

i want that to appear right when i log on.  I think i have to put it in the logon directory:confused:????? Thanks for the help so far

---

### Post by Adaptor on 2008-01-06
> **Dr Small said:**
> Are you wanting the script to run as soon as you login or appear on your desktop ?

o.ummmmm login is where i was aiming at. Is there a certain directory for logging on? If there is whats it called?

---

