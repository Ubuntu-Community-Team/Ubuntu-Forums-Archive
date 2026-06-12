---
title: "what graphics card driver do i need ?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by dbbolton on 2007-01-20
i'm completely ignorant 
(running edgy) :

---

### Post by BarfBag on 2007-01-20
You need the nVidia driver.  For a newbie, the easiest way to install it is through [Automatix]("http://www.getautomatix.com/").  You can also install it [manually]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29").

---

### Post by xpod on 2007-01-20
You could always try the ones from here if thats all you need

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

---

### Post by dbbolton on 2007-01-20
according to my xorg, i have NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] 

(apparently i'm using the nv driver right now)

i've been to the nvidia site already, but i don't know which version of the nvidia driver i need. also, does the nvidia driver work with openGL ?

---

### Post by BarfBag on 2007-01-20
> **dbbolton said:**
> according to my xorg, i have NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] 

(apparently i'm using the nv driver right now)

i've been to the nvidia site already, but i don't know which version of the nvidia driver i need. also, does the nvidia driver work with openGL ?

That's correct.  By default, Ubuntu comes with an open source driver for nVidia/ATI cards.  The problem is - it doesn't support 3d acceleration.

Since you're a newbie, you should definitely install the driver with [Automatix]("http://www.getautomatix.com/").  You punch in a few commands to install it (which the website gives you), then simply check the box next to "nVidia Driver."  It does everything for you.  You can also install things like MP3 support, DVD support, etc.

Yes, the nVidia driver does support OpenGL.

---

### Post by dbbolton on 2007-01-20
i'm not really a complete newbie. i've had beryl working as XGL on an ATI machine and as XGL on this one, but it mysteriously died so i'm going to try compiz- i just didn't know which version of 'NVIDIA-Linux-x86-#####-pkg1.run' that i needed to download

thanks for the suggestion, but i prefer to do things manually over automatix when i can, because i dont want to get too lazy/dependent on it ;)

---

