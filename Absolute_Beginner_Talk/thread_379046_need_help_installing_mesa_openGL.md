---
title: "need help installing mesa openGL"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by CircaSurvivor on 2007-03-08
i was trying to run planeshift but it said indirect rendering may indicate a flawed openGL setup so i tried to get a new openGL for my pc.  i went to get mesa, but i have no idea how to install it, even after reading instructions.  please help

---

### Post by nereid on 2007-03-08
Mesa is the default software OpenGL implementation. It should be installed by default with the Xserver. Which kind of graphic card do you own?

---

### Post by CircaSurvivor on 2007-03-08
nvidia geforce 5200

---

### Post by nereid on 2007-03-08
So, why don't you use the nvidia graphics driver? They will even use your hardware. Mesa OpenGL is the last resort and emulates OpenGL on your processor. This means, that the resulting graphics are sloppy and won't look so nice (if you don't own a real good duo or quad core system ;) ).

---

### Post by CircaSurvivor on 2007-03-08
wait, so all i have to do is download the drivers for my card on the nvidia website?

---

### Post by Perfect Storm on 2007-03-08
Or the more simple way installing it via synaptic/apt-get/aptitude ;)

---

