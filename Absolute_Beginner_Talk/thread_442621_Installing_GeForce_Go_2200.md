---
title: "Installing GeForce Go 2200"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by draegoonscythe on 2007-05-13
Hey,

I'm a starting Linux user, and i was trying to install my NVIDIA graphics card on the computer. Every time I try it always says I have to exit the X-Server first. I tried doing 

sudo /etc/init.d/gdm stop

but then I get a message that says that the server on :0 has stopped, and should it look for another display number. I'm not too sure exactly how to get X-Server to stop. Can anyoen help?

---

### Post by RomeReactor on 2007-05-13
Hi. Did you **CTRL+ALT+F1** *before* running **sudo /etc/init.d/gdm stop**? Also, have you tried installing the drivers from Synaptic? The easiest way I found in Feisty is to try to enable Desktop Effects and it will ask you if you'd like to install the restricted drivers; I said yes and afterwards I even had 3d acceleration enabled, just like that.

---

