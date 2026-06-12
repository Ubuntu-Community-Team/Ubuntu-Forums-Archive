---
title: "re; compiz - where to get libGl.so.1?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-11-27
[FONT="Comic Sans MS"]I've been following the wiki guide here > [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
to set up a new install with compiz (last one went belly up) and I got to the part where it says;
> If it says  libGL.so.1: cannot open shared object file: No such file or directory... Check if you have a /usr/lib/libGL.so.1.2, if so do this:
The problem is I don't have it. This eventuality is not covered in the wiki.
So, where can I get this file?
I'm guessing I had it before as now that I've followed this guide Amarok is no longer starting up.
Synaptic, Sourceforge and Apt don't have it.
Thanks.[/FONT]

---

### Post by Nano Geek on 2007-11-27
See if this fixes it.```
sudo apt-get install libgl1
```

---

### Post by carloslosgrande on 2007-11-28
Thanks asjd....etc
Tried that and got this;
ramses@memphis:~$ sudo apt-get install libgl1

Package libgl1 is a virtual package provided by:
  libgl1-mesa-glide3 6.2.1-8.1
  libgl1-mesa-swx11 7.0.1-1ubuntu3
  libgl1-mesa-glx 7.0.1-1ubuntu3
You should explicitly select one to install.
E: Package libgl1 has no installation candidate

looked in synaptic - mesa-glide and mesa-swx1,  installation of either means removal of ubuntu-desktop and mesa-glx and mesa-dri.

---

### Post by Nano Geek on 2007-11-28
Try installing this.```
sudo apt-get install libgl1-mesa-glx
```

---

### Post by Firestone on 2007-11-28
There's a file libGL.so.1.2.xlibmesa in your /usr/lib/nvidia
Copy that file to /usr/lib and rename it to libGL.so.1.2 and it will probably work.

---

