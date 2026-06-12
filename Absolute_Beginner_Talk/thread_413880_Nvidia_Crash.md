---
title: "Nvidia Crash"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by phelixnyc on 2007-04-19
I just installed Feisty and am encountering crashes every time I boot. After I press the reset button on my rig it boots fine. When it crashes I get this weird color thing going on the screen I am assuming it has something to do with my x-server(I may be wrong). Where do I start to correct my problem? Thanx

---

### Post by Seisen on 2007-04-19
How did you install the ndivida driver before?

---

### Post by phelixnyc on 2007-04-19
I used automatix2 for Feisty and for Edgy.

---

### Post by K.Mandla on 2007-04-19
What kind of video card do you have? If you edit the /etc/X11/xorg.conf file to use "nv" instead of "nvidia", does that help?

---

### Post by phelixnyc on 2007-04-19
Nvidia 7600 GT OC and I'll try but I cant right now.

---

### Post by zubrug on 2007-04-19
install nvidia-glx-new, nvidia-glx is now for geforce4 or older I believe.

---

