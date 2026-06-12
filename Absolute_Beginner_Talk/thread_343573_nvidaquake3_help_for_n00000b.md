---
title: "nvida/quake3 help for n00000b"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by jared234 on 2007-01-21
trying to load up q3 on edgy and i can not do it. i used the SPM nvidia install to update my drivers, and it still wouldnt work, then i used([http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) and im still getting the same error: Sys_Error: GLimp_Init() - could not load OpenGL subsystem

Do you know how i can fix this?

---

### Post by crane on 2007-01-21
What is the SPM nvidia install? I am not familiar with that.
I'm pretty sure apt-get install nvidia-glx was the best way to install drivers.

---

### Post by jared234 on 2007-01-21
synaptic package manager

---

### Post by jared234 on 2007-01-21
synaptic package manager, also now when i do the glxinfo | grep command it says: Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.



its kinda disturbing, and i dont know what to do

---

### Post by crane on 2007-01-22
I'm a bit confused. SO you are saying you DID install nvidia driver through synaptic. Did you check and make sure you xorg.conf file has been changed?

---

