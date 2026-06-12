---
title: "[SOLVED] Accessing USB stick from Terminal"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by punkle on 2007-11-20
Hi,

I have a USB stick named UDISK 2.0.

I have tried to access it from the terminal using 

cd /media/UDISK 2.0/

I get the error message

punkle@punkle-desktop:/media$ cd /media/UDISK 2.0
bash: cd: /media/UDISK: No such file or directory

Could someone help me with this.

Thank You

b

---

### Post by Inxsible on 2007-11-20
Are sure that the mount point of the stick is UDISK 2.0?

If yes, then you need to compensate for the space in between. Try this:
```
 cd /media/"UDISK 2.0"
```This would work too```
cd "/media/UDISK 2.0"
```Notice that the quotes are around the entire path this time.

---

### Post by punkle on 2007-11-20
worked like a dream,

thank you

b

---

### Post by Inxsible on 2007-11-20
> **punkle said:**
> worked like a dream,

thank you

byou are welcome !

mark your thread as solved. Thread Tools>>Mark thread as solved

---

