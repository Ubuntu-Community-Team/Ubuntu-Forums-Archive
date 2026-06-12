---
title: "Fiesty nvidia drivers"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by eduardoeltortuga on 2007-04-27
Can I download and install the new nvidia drivers from the tty screen?  I can't get to the GUI screen without the drivers. That is the way I had to do it with Edgy. Is there a website that will give me step by step instructios to do this. I don't have onboard video. If you need more info to help me please let me know:( .


          Thanks

---

### Post by kpkeerthi on 2007-04-27
1. sudo aptitude install nvidia-glx-new nvidia-kernel-common
2. sudo nvidia-xconfig

and restart PC

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by eduardoeltortuga on 2007-04-27
thanks, but i just get a message saying "cannot open display."

---

### Post by xyphur on 2007-04-27
Assuming you have a fairly new nvidia graphics card, type the following:

wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)

(replace the URL above with [http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run) for 64-bit machines)

It'll downlad the .run package to the current working directory, so it'd be wise to stay in your home directory when issuing the above command. After it's finished, type the following:

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

(or NVIDIA-Linux-x86_64-1.0-9755-pkg2.run, if 64-bit)

Follow the on-screen instructions...

Also, if this is an upgrade from Edgy, and not a fresh install of Feisty, you'll likely need the 'new' kernel-source package as well to match your current kernel so the NVIDIA installer can compile kernel interface modules for you. Your mileage may vary, depending on what type of card/chipset you have, and whether the NVIDIA ncurses installer can locate proper kernel-sources to compile a new kernel interface module for you... if it runs into problems, it'll tell you pretty plainly what went wrong. There are a couple threads here about insuring you have the correct packages for this on-the-fly compilation to take place, if necessary.

Hope that helps... good luck!

---

