---
title: "[SOLVED] PROBLEM with Gutsy and Cadsoft Eagle"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by antonio.spadim on 2007-10-31
Hello you all,

   At first, I'm using Ubuntu 7.10 Gutsy Gibbon and a NVIDIA Video Card.

   I'm trying to run **eagle** pcb program. I installed it using synaptic, but when I tryed to run the eagle's painel control, schematic and board window have no background!!!!

   It looks like that was removed the white screen in the background. I attached a screenshot with my desktop. 

   Does somebody know how to fix this bug?

Thanks,
Antonio

---

### Post by haldean on 2007-10-31
That's most likely a bug with the program itself - you should contact the developers of eagle.
It might be an issue with a compositor tho... if you're running compiz or beryl try disabling it and see if the same thing happens.

---

### Post by antonio.spadim on 2007-10-31
Yes! It works... if I disable compiz it works fine.

Thank you haldean,
Antonio

---

### Post by antonio.spadim on 2007-10-31
Can I disable compiz only to eagle? Only it has problems with compiz... :P

---

### Post by haldean on 2007-11-01
As far as I know, there's no way to do that. You'll have to completely disable it whenever you use Eagle.

Glad that helped, though!

---

### Post by gheorghe_pop on 2007-11-11
Hello,

I had the same problem. Check [http://minipop.org]("http://minipop.org") for the solution.

---

### Post by antonio.spadim on 2007-11-11
Thank you gheorghe, it works perfectly.

UBUNTU ROCKS
:guitar:

---

### Post by dwar on 2007-11-13
What it exactly dus, I don't know... but its works.

start eagle with the commandline with XLIB_SKIP_ARGB_VISUALS=1 /usr/lib/eagle/bin/eagle

---

### Post by antonio.spadim on 2007-11-14
Ok... 

   dwar, the gheorghe solutions is so similar as yours, that works too.

---

