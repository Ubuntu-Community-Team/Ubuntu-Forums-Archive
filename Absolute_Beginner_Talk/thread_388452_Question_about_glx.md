---
title: "Question about glx"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by russianbandit on 2007-03-19
What is glx as far as nvidia video drivers are concerned?
Baically, why do i need nvidia-glx?
I'm also wondering about nvidia-glx-xconfig and nvidia-xconfig commands, what does one do that the other doesn't?

Thank you.

---

### Post by Stickymaddness on 2007-03-19
Hi,

You will need to install "nvidia-glx" in order for your graphics card to work 100%. This obviously assuming that you have an nvidia graphics card!

---

### Post by Bachstelze on 2007-03-19
The nvidia-glx package contains the GLX libraries required to have 3D acceleration with nvidia cards as well as the nvidia Xorg module.

The nvidia-xconfig and nvidia-glx-config comands are used to configure your Xorg to run the nvidia driver. I don't know what the differences between them are but as far as Ubuntu official packages are concerned, nvidia-xconfig is used in Edgy and nvidia-glx-config in older Ubuntu releases.

---

### Post by r4ik on 2007-03-19
Try,

glxgears -printfps

It will show you you're framerate.

---

