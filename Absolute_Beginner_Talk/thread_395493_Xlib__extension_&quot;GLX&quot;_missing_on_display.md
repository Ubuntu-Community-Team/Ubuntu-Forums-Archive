---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2007-03-28
I have installed nvidia-glx_1.0.8776nvidia-glx_1.0.8776+2.6.15.12-28.1_amd64.deb
nvidia-glx_1.0.8776+2.6.15.12-28.1_amd64.deb
+2.6.15.12-28.1_amd64.deb
on my Ubuntu 6.06 to do OpenGL programming. However, I get the following errors when I try to run an OpenGL program I have written. I have also given the output of 'glxgears'.

```
smith@everest:~/OpenGL/lesson01$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
smith@everest:~/OpenGL/lesson01$ ./a.out
freeglut (./a.out): OpenGL GLX extension not supported by display ':0.0'
```

Please let me know how I can remove this error and continue see the output of my OpenGL programs.

---

### Post by bradleyd on 2007-03-28
in your xorg.conf, under Section "Device", what is the driver you have listed nv or nvidia?

---

### Post by smith.norton on 2007-03-28
I don't know. I will have to go home and check. I don't have internet at home, so I can post it tomorrow only.

I also have another strange problem. When I installed the nvidia graphics driver from the NVidia site (NVIDIA-Linux-x86_64-1.0-9755-pkg2.run), It replaced xorg.conf file.

After that when I rebooted, my X crashed every time. Finally, I had to replace this xorg.conf with the xorg.conf.backup.

Any idea what's the problem here?

---

### Post by deuchar1 on 2007-03-28
I always say the same thing - I know it doesn't work for everybody, but it works in most cases with nvidia/ati drivers - run a script called Envy.

You can firstly use it to uninstall all the dud nvidia installed information, then run a fresh install which will automatically download/install/configure all necessary drivers to get the card working with opengl support.

---

### Post by bradleyd on 2007-03-28
check to see what your errors X is giving when it crashes. Also when you revert back to old xorg.conf file it is probably using driver nv(open source nvidia driver)and that is where your problems lie with glxgears.

---

### Post by smith.norton on 2007-03-29
> **bradleyd said:**
> check to see what your errors X is giving when it crashes. Also when you revert back to old xorg.conf file it is probably using driver nv(open source nvidia driver)and that is where your problems lie with glxgears.

My old xorg.conf did not have any "Device" section. In my new xorg.conf, it is "Nvidia".

---

### Post by smith.norton on 2007-03-29
Where can I find the error log for X?

I am completely lost due to this GLX trouble. But I want to start OpenGL. I would like to start configuring everything afresh. How should I undo whatever I have done and start afresh?

---

### Post by bradleyd on 2007-03-30
ok new xorg.conf is the one you need to use.  Also when you start with new xorg.conf what happens, does the screen go black, flicker, do you get this [IMG]http://img134.imageshack.us/img134/8596/3800yq1.jpg[/IMG]
you Xorg error log is under /var/log/Xorg.0.log(or depending on the number of logs rotated)

---

