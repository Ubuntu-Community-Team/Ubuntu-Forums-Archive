---
title: "Beryl Not Loading Correctly"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by arcarsination on 2006-12-09
Hey everyone,

I've recently tried installing Beryl on edgy eft, with an amd64 and nvidia. I followed the instructions on this site [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) making sure that I followed the nvidia instructions.  I can get into xgl and can make beryl start, but all that I see is the sys tray icon and all of the options that come along with it.  

I have metacity selected as the window manager right now because every time I put it as beryl, the frames around the windows disappear.  There is no splash screen when it starts, as said in the instructions.  All i get is the sys tray icon and the options, with no effects at all.

any help would be awesome. thanks.:-?

---

### Post by igknighted on 2006-12-09
My recomendation:

Remove XGL and try running beryl from a normal session.  NVIDIA can use the native AIGLX, which is less invasive and performs better than XGL.  Make sure you have the latest NVIDIA driver though, something that ends with 9xxx and not 8xxx.

---

### Post by arcarsination on 2006-12-09
i know this sounds stupid... but how do i check to see what drivers i have installed?  I have automatix and i'm pretty sure that installed the latest ones just yesterday...

---

### Post by hanzomon4 on 2006-12-09
Download the latest Nvidia driver ([Linux IA32]("http://www.nvidia.com/object/unix.html")?) 
Then switch to ctrl+alt+F1 and kill x ```
sudo /etc/init.d/gdm stop
``` Then cd to the desktop ```
cd ~/desk{press tab}
``` then run the installer ```
sudo sh NVIDIA{press tab}
``` Last restart X ```
sudo /etc/init.d/gdm restart
```

If you have more then one kernel you have to repeat the install for each kernel and add the -K option to the end ```
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run -K

```

---

### Post by astoltz on 2006-12-09
You can see what version you're actually running with the following:

```
cat /proc/driver/nvidia/version
``` 

The first line has 1.0-xxxx someplace in the middle - the xxxx is the driver version.  Mine spits out 1.0-9629 for example.

---

