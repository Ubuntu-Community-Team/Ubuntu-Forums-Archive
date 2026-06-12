---
title: "x server won't work following updates"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by bumanie on 2008-02-13
Using feisty fawn. Today, I downloaded 4 updates which included ubuntu headers. Now I can't get past the splash screen. Get a message that x server can't start and the nvidia drivers are the wrong ones. Then it goes to console mode. Does anyone know what codes need to be put into console? I tried  > sudo dpkg-reconfigure -phigh xserver-xorg, but that did not help.
System amd 2600+ 1gig ddr ram nvidia mx4000 agp video card.

---

### Post by PmDematagoda on 2008-02-13
You may have to reinstall the Nvidia drivers, could you please specify as to how you installed the Nvidia drivers in the first place?

---

### Post by bumanie on 2008-02-13
Originally installed via restricted drivers. A couple of days ago, I tried to get compiz-fusion working and installed the driver in console by stopping gdm, installing the .run driver (96.43.05) from the nvidia site and restarting gdm. I am presently using the live cd to use the internet. I am unable to reinstall the driver that way because I don't have the .run file on the computer anymore.

---

### Post by PmDematagoda on 2008-02-13
Boot Ubuntu in Recovery Mode and execute this:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/NVIDIA-Linux-x86-96.43.05-pkg1.run
```
That will download the Nvidia driver to the current directory after which you can start the installation using:-
```
sh NVIDIA-Linux-x86-96.43.05-pkg1.run
```

---

### Post by bumanie on 2008-02-13
I don't get as far as being able to choose recovery mode, as soon as the drivers etc load, I get the error messages. Will this work from console which is where I get to once I have gone through the error messages?

---

### Post by PmDematagoda on 2008-02-13
Yes it should work that way as well, but are you sure that you chose Recovery Mode? Since no GUI is loaded on Recovery Mode by default you should not receive any messages about the Nvidia driver failing.

---

