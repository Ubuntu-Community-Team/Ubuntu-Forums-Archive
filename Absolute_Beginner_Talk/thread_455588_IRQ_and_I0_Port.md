---
title: "IRQ and I0 Port"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by playswithdogs on 2007-05-26
I installing LIRC and i need to know the IRQ and I0 port number for my serial device how can i find these

---

### Post by bernied on 2007-05-26
I'm not completely sure of what you are asking for, but you could try this:
```
sudo dmesg | grep serial
```
dmesg shows kernel messages (try it on its own), the command above pipes the results to grep, which just looks for lines with 'serial' in them.

Does that help?

---

