---
title: "Stupid old AGP NVidia graphics card"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by G_force on 2007-02-13
I want to add a screen res to my computer as ubuntu is currently running in 800 x 600 which is impractical for most tasks

i tried installing the nvidia drivers and i don't know which ones i need.

i have tried it a number of times and everytime have failed miserable and have use the non graphical interface that i have no idea how to use and reinstate the nv instead of nvidia x.config file i think

any help would be greatly apprieciated

---

### Post by Tmi on 2007-02-13
I'm not really sure about what to do, but have you tried installing the nvidia-glx package, then typing "nvidia" instead of "nv" in the driver of your graphics card in your x-config? If you get an nvidia-logo while starting X all you need to do thereafter is add the resolutions in your x-config.

But as I said, I'm not really sure. That's what I did though.

---

### Post by Perfect Storm on 2007-02-13
You need to install nvidia-glx-legacy (old nvidia cards). Change "nv" to "nvidia". See if it helps.
If it fail 
sudo nano /etc/X11/xorg.conf
to change it back.

---

### Post by G_force on 2007-02-13
you guys are legends cheers

---

