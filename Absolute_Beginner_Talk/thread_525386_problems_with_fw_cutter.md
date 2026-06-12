---
title: "problems with fw cutter"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by drascus on 2007-08-14
I am having trouble with fw-cutter bcm43xxx install. I have installed it before with no problems on this hardware. I am using a fresh install of feisty 7.04. I have attached a copy of the error message and terminal readout. for some reason it won't extract the firmware make my hardware function.

---

### Post by deadgobby on 2007-08-14
Are you installing this with Automatix? 
Gobby

---

### Post by drascus on 2007-08-14
I installed it through synaptic I am not sure if that is considered automatix though

---

### Post by drascus on 2007-08-14
Just to let the group know I was able to resolve this issue by manually installing the firmware. I don't know what is wrong with the fw-cutter that is in synaptic but it seems that it is not connecting to the right website where the firmware is located. my only question now is there a place where I can report this to get it resolved by the maintainers of that code?

---

### Post by fraser_m on 2007-08-14
I had the same problem, I had to connect to a Ethernet  socket to do it. It would be nice if the developers would let you download easily on a networked PC and then be able to grab the firmware from a local drive e.g. USB stick.

---

### Post by Kedster on 2007-09-16
to get rid of the fw-cutter

try this

```
sudo apt-get remove --purge bcm43xx-fwcutter
```
it worked for me and now i can install things

---

