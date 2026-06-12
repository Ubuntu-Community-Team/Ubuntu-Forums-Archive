---
title: "Is my hardware installation succesful??"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-24
Hi I just bought a PCI card with 3 serial ports, 2 db9 and 1 db25......However I dont know how to check whether this install was succesfull or not. All I have done is put it on my motherboard, Is there something I have to do now? Also how do I find out the new port names of my newly installed card???

---

### Post by tommcd on 2006-12-24
Try looking in the device manager (system>administration>device manager. Also try these commands in terminal:
lshw (list hardware)
lspci (list PCI devices)
hopefully you should find it listed. If not I'm not sure how to install something like that.

---

### Post by Malta paul on 2006-12-24
I use HARDINFO and find it good.
You can find it in Applications>Add/remove>system tools> tick the Hardinfo box then click Apply.
Hope this is of some help   ;)

---

### Post by nite owl on 2006-12-24
thanks Malta paul and tommcd for your input and I am downloading hardinfo as I type this :) however would anyone know of a command/commands that would bring up the node names of all my ports??i.e ttys7????????

---

