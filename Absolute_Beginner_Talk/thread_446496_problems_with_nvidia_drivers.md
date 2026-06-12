---
title: "problems with nvidia drivers"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by sephirot_5 on 2007-05-17
hi everybody, i hope someone can help me.

I have just installed feisty and everything's great, but i have some problems with the nvidia drivers. You'll see, i am using a nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (as my xorg.conf says)

The problem i think, is that the default nvidia drivers are tooooo new for my poor card; whenever i enable them, everything gets too buggy; and sometimes x crashes randomly.

I had none of these problems with the (propietary) drivers for edgy. Can anyone help me? Is there a way to install older drivers?

Thanx ;)

---

### Post by nicepants on 2007-05-17
i do know that nvidia provides legacy drivers [here]("http://www.nvidia.com/object/unix.html"), though i use new hardware and couldn't help you out with the config/install.

good luck! =D

---

### Post by Nythain on 2007-05-17
sudo apt-get install nvidia-glx-legacy

---

