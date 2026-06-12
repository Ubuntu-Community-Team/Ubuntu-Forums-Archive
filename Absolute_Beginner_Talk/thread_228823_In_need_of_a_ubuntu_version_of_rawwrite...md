---
title: "In need of a ubuntu version of rawwrite.."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-08-03
I had this in windows and it worked flawlessly..

[RawWrite-Win]("http://www.chrysocome.net/rawwrite")

[IMG]http://www.chrysocome.net/images/rawwrite-thumb.png[/IMG]


but i need something like this in ubuntu...


Anything like this out there...???   :-k

---

### Post by ajgreeny on 2006-08-03
Probably all you need to use is the command dd in a terminal, but it may depend on exactly what you want to do.  Let's have more info and we'll be able to help, I hope.

---

### Post by jason.b.c on 2006-08-03
> **ajgreeny said:**
> Probably all you need to use is the command dd in a terminal, but it may depend on exactly what you want to do.  Let's have more info and we'll be able to help, I hope.


Well i need something that i can interact with a little more that the "Terminal" , ya know what i mean..??

Like click this button , click that button , "done" "written"....

A nice GUI application...:D

---

### Post by jason.b.c on 2006-08-03
*Bump*

---

### Post by jason.b.c on 2006-08-03
*Bump*

---

### Post by deanlinkous on 2006-08-04
too much bumpin going on in here for me :)

---

### Post by jason.b.c on 2006-08-04
> **deanlinkous said:**
> too much bumpin going on in here for me :)

Oh really now...?  =D>

---

### Post by jason.b.c on 2006-08-04
Well, Guess i'll try this again...:-({|=

---

### Post by Brunellus on 2006-08-04
If you're using KDE, there's kfloppy.

Is there not a "floppy formatter" in your System menu?

otherwise, as other people have noted, use dd.

---

### Post by steve.horsley on 2006-08-04
If you're prepared to use dd, there are lots of people who can help. frinstance:
**dd if=floppy.img of=/dev/fd0**
You may need to use this to get the permissions:
**sudo dd if=floppy.img of=/dev/fd0**

But if you insist on having a GUI, you wil probably have to wait until someone writes one. Why would anyone write a GUI to replace a one-line command though?

---

### Post by jason.b.c on 2006-08-04
> **Brunellus said:**
> If you're using KDE, there's kfloppy.

Is there not a "floppy formatter" in your System menu?

otherwise, as other people have noted, use dd.

Yes i have the formatter...

Raw-write isn't a formatter , it's a floppy image writer....**.IMG**..

---

