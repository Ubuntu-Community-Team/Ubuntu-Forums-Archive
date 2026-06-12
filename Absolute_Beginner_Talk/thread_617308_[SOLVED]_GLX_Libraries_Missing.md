---
title: "[SOLVED] GLX Libraries Missing"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by kspn on 2007-11-19
I have just replaced by system and I have kept the install of Xubuntu.

This has worked without a hitch except for one component.

The old system had a NVIDIA card in it and so I was using the NVIDIA GLX Libraries, now I have an Intel i810 chip set and I cannot get the GLX/OPENGL systems to function.

Anyone know what I need to re-install to get the 3d functional again?

---

### Post by vinutux on 2007-11-20
.....................

try at ur own risk..................

but may be works

1. back up /etc/X11/xorg.conf

2 remove /etc/X11/xorg.conf [in termianal "sudo rm /etc/X11/xorg.conf"]

3 restart system or type "startx" [without quatos]

............................it reconfigure ur correct graphics cadrd:guitar::guitar::guitar:

---

### Post by kspn on 2007-11-20
I have tracked down the issue and it appears that the libGL.so.1 file is missing, 

I am unable to work out where to locate the file for re-deployment to my system.

---

### Post by schorsch on 2007-11-20
/usr/lib/libGL.so.1 is just a link to /usr/lib/libGL.so.1.2 which is part of the package libgl1-mesa-glx

---

### Post by kspn on 2007-11-20
The libgl1-mesa-glx package is installed but the libGL.so.1.2 (and libGL.so.1) files are still missing :(

---

### Post by schorsch on 2007-11-20
Are you running a 32 or 64 bit OS? If it is a 64 bit OS the files should be in /usr/lib64 .....

---

### Post by kspn on 2007-11-20
I am running a 32 bit OS.

I can see the symbolic link from libGL.so to libGL.so.1 but the libGL.so.1 file itself is missing and I cannot locate it.

I suppose this is what I get for pushing a button with the idea of 'What is the worst that can happen?'

I either need a copy of the file (appropriate to a 32-bit i810 video Driver) or info on how to get Ubuntu to re-install the file itself :confused:

Thanks for all the help guys :D

---

### Post by schorsch on 2007-11-21
What happens if you reinstall the whole package via
```
sudo aptitude reinstall libgl1-mesa-glx
```

---

### Post by kspn on 2007-11-21
Nothing, I have managed to fix the problem by running 
```
apt-get install nvidia-glx
```
This has done the trick.

---

### Post by schorsch on 2007-11-21
Alright, glad to hear that you solved your problem. Could you please mark this thread as solved as it may help others, too? But it is really weird that you have to install an nvidia package to get an Intel card up and running ....

---

### Post by kspn on 2007-11-22
It is still a bit flaky depending on which System Kernel I use but it is overall Functional.

---

