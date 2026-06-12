---
title: "Possible corrupt video driver"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-15
I think that my video driver may be corrupt. When I attempted to preview a screen saver, the screen went blank for a moment and I was taken back to the login screen. 

I am using the Nvidia driver from nvidia's website. It came in the .run format which I installed at the command line. How can I uninstall this driver so that I can re-install it?

---

### Post by Bekker on 2007-04-16
I'm not sure whether reinstalling the driver will help.
But I can tell you how to uninstall the NVidia driver:
You'll need the original file you downloaded from the nvidia site, if you don't have it on you computer anymore download it again (making sure you download the same version).
Then execute
```
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run --uninstall
```
(That's the command you used to install it with the --uninstall option)
9755 is the version of my current nvidia driver, you'll have to change that into your verisonnumber.

---

### Post by TURNER on 2007-04-16
possible openGL problem maybe?

If you open a terminal and run:

```
glxgears
```

do you see 3 spinning cogs??

---

