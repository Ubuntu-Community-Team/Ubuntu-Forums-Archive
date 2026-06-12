---
title: "termcap not found"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by ahaider on 2008-04-13
I want to compile the package asterisk-1.4.2 but while executing **./configure**, it gives me the error:

termcap support not found.

How can I get it ?

---

### Post by halitech on 2008-04-13
from a terminal type 
```

sudo apt-get install build-essential

```
and that shoudl install all you need

---

### Post by anewguy on 2008-04-14
And, if you are wondering what termcap is, it is a file describing different physical terminals and the things they support - line graphics, certain key command sequences, etc.  At least that is what that file has been in the past.  You could log on to Unix and say your terminal type was VT320, for example, and it would find everything that a physical VT320 terminal could do and the command sequences for things.  I really don't know if this is used much anymore, since everything has pretty much moved over to the PC world.  In the "old" days I come from, when we didn't have PC's yet (they actually did not exist!), and instead used various physical terminals.  We could set a brand "x" terminal up to emulate a VT100, VT320, various IBM, Honeywell, etc., terminals, then connect to Unix and tell it the terminal type so everything would run the same from one terminal to the next.  Believe me, in those days you could easily spend $3000 for certain vendor terminals.  When you could find a $350 terminal that would emulate one of the terminal types supported, you went with the $350 terminal.

If the usage/meaning of this file has changed since those days, could someone pass along to me what is different now?  While I no longer work, I am still curious of such things.

:)

---

### Post by ahaider on 2008-04-14
> **halitech said:**
> from a terminal type 
```

sudo apt-get install build-essential

```
and that shoudl install all you need

oops !!!!!!!!!!!! That dosn't work.

I have installed  **build-essential** correctly, but still it is giving me same error: :mad:
*** termcap support not found.

What the solution now ???

---

