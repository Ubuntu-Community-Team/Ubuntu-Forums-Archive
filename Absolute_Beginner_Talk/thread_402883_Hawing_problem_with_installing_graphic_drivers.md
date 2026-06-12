---
title: "Hawing problem with installing graphic drivers"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-04-06
:confused: Helllo

I tried to install latest Nvidia drivers but I'am having some problems. Fist I'd download latest NVIDIA-Linux-x86-1.0-9755.pkg1.run and save them on my home folder.Than I run it in terminal with "sh NVIDIA-Linux-x86-1.0-9755.pkg1.run" command. Terminal writes me thah this drivers must be installet as a root.
Secont thing I done was thah I run command "sudo -i" to get to root.But if I tried to run Nvidia drivers in root with "sh NVIDIA-Linux-x86-1.0-9755.pkg1.run" command, terminal give me an following error "couldn't open NVIDIA-Linux-x86-1.0-9755.pkg1.run package":( 
Now I don't know what to do? Can enybody please tell me how to properly install selected graphic drivers:confused: 

Thanx

---

### Post by Maestro23 on 2007-04-06
In terminal:

> chmod a+x filename.run

sudo ./filename.run

You can also try the Envy script: Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

