---
title: "Nvidia driver"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by plo--koon on 2007-03-06
Hi all,

I a me using ubuntu for a week and it's a nice os but ... I have a problem.

(I updated my graphics card and reboted but i got this)

```
Failed to start X-server (graphical interface)
Xserver out put to diagnose? Y
```

and here are the errors
```
- failed to load module "wfb" (module does not exist, 0)
error api mismatch: the NVIDIA kernel module has version 1.0-8776, but this x module has version 1.0-9746

- NVIDIA(0): faild to initialze the NVIDIA kernel module. 
Pleas ensure there is a supported NVIDIA GPU and has NVIDIA deevice files have been overated properly

- screen(s) found, but none have a usable configurtion

Fatal server error:
no screens found
```

---

### Post by Shatrat on 2007-03-06
How did you install the driver?
The kernel module interface between the driver and kernel is of version 8776, the one in the normal ubuntu repos, and the driver you have installed is 9746, which is only found in special repositories.

---

### Post by endtroducing on 2007-03-06
Hi!

Try this script: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by r4ik on 2007-03-06
press Control-Alt-F1 and try

sudo dpkg-reconfigure xserver-xorg

Follow the defaults,

Set you're video driver to nv

finish with,

sudo /etc/init.d/gdm start

Use the script suggested and you should be oke.

Good luck !

---

