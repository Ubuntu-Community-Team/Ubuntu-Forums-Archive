---
title: "[SOLVED] system priority"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by potatoehead64 on 2007-06-11
Things are coming along quite well. I've managed to install on 2 machines. I'm keeping XP so that myself and my kids can Mr Gates games etc. I noticed that I have to manually select Windows XP within a few seconds, otherwise Ubuntu will boot by default. I've tried looking at the BIOS to see if I can change this without success. It's a little annoying because I'm (for now) still using XP as a priority. Any idea how to change the above?

---

### Post by sailor2001 on 2007-06-11
to change your boot loader:  sudo gedit /boot/grub/menu.lst    Change your default (it's at 0 right now) to the number of your xp. Start counting down from 0 (ubuntu generic) to your xp in start-up screen and change the 0 to that number

---

### Post by taurus on 2007-06-11
You can edit /boot/grub/menu.lst and set your XP as a default.

Applications -> Accessories -> Terminal
```
gksudp gedit /boot/grub/menu.lst
```
Change the 

```
default     0
```
to whatever entry your XP is.  Remember, each line that starts with title counts as one and you start counting from 0, i.e.  first title is 0, the second title is one...

You can also increase the timeout from 3 seconds to longer if you wish.

```
timeout     10
```

---

