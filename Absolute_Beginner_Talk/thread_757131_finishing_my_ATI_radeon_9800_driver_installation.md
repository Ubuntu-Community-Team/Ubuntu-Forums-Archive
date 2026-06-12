---
title: "finishing my ATI radeon 9800 driver installation"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Aciid Bu5t0r on 2008-04-16
i've been fooling around with several guides on how to install the latest drivers from ati.com for my video card on my Ubuntu 7.10 installation. i really really thought i could manage to do without asking for help here, but it looks like i'm stuck on the very last bit :(

so i installed these fglrx proprietary drivers, and after hours and hours of troobleshooting i finally got my computer to run with accelerated 3D and 1280x1024@75Hz settings (you have no idea how much of a pain it has been. this stupid thing kept booting into low graphics mode with Vesa drivers, whatever they are)

so i suppose i'm near the end, but when i try to run glxinfo or glxgears it pops up this error
```
error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

so i googled where this file should be located and i found this usefull command "dpkg -S libGL.so"
i'm a bit clueless on what it does exactly, but it popped up this: (dutch ubuntu installation)

```
verwijzing door xorg-driver-fglrx van: /usr/lib/libGL.so.1.2
verwijzing door xorg-driver-fglrx naar: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
verwijzing door xorg-driver-fglrx van: /usr/X11R6/lib/libGL.so.1.2
verwijzing door xorg-driver-fglrx naar: /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa
verwijzing door xorg-driver-fglrx van: /usr/X11R6/lib/libGL.so.1.2
verwijzing door xorg-driver-fglrx naar: /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa
verwijzing door xorg-driver-fglrx van: /usr/lib/libGL.so.1.2
verwijzing door xorg-driver-fglrx naar: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
xorg-driver-fglrx, libgl1-mesa-glx: /usr/lib/libGL.so.1.2

```

i browsed to those locations and i saw that those files were renamed. they were probably driver files for this Vesa thingy? so i suppose i must now replace them with the files for the ati fglrx drivers.. but then where can i find those?

tell me if i made some kind of mistake somewhere, any help is appreciated..

---

### Post by talsemgeest on 2008-04-17
You are unning 64bit arent you? Take a look here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Hope this helps :)

---

### Post by Aciid Bu5t0r on 2008-04-17
nope, im running 32bit :/

anyways it did have a terminal command i haven't seen anywhere else before

>     *  Check the permission of the libGL.so.1.2 file with command: 

 ls -l /usr/lib/libGL*


so i did that and it popped up this
```
lrwxrwxrwx 1 root root 17 2008-04-16 22:59[COLOR="Red"] /usr/lib/libGL.so.1[/COLOR] -> /usr/lib/libGL.so

```

i'm clueless on what that means, but anyone can tell that "/usr/lib/libGL.so.1" being marked in red isn't a good thing..

EDIT: so many people are recommending to copy/paste this in a terminal 
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```
and say that afterwards everything should be okay, however this does not work for me :(

---

