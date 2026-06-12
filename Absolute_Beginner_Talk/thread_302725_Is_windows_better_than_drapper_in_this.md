---
title: "Is windows better than drapper in this?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-19
Hi everybody.

I was wondering if Drapper drake can support multiple cut and paste transactions, so that I can do several copies of several sentences and then add them in a new file all together. But I don't think there is a clipboard can do this, so as far as I could see (I've tried Tomboy), but maybe there is a way out ...

Thanks for any hint

---

### Post by jaboua on 2006-11-19
I believe "klipper" can hold lots of different copies, but that's a KDE application (kubuntu) so I'm not sure if it works OK in gnome (normal ubuntu), or if it even is a desirable solution (you might have to load lots of KDE services in the background)

---

### Post by helphope on 2006-11-19
Thanks for replying, but I've seen other posts that confirm what you say (apart form the fact that it doesn't work)

---

### Post by namah on 2006-11-19
This might be what you are looking for

[http://glipper.sourceforge.net/](http://glipper.sourceforge.net/)

---

### Post by urukrama on 2006-11-19
If you use gnome, try glipper. It is like klipper, but for gnome. It is in the repositories, so either type 

```
sudo apt-get install glipper
```

in a terminal, or select the appropriate package in Synaptic.

---

### Post by helphope on 2006-11-19
> **namah said:**
> This might be what you are looking for

[http://glipper.sourceforge.net/](http://glipper.sourceforge.net/)

Thanks. It seems so, but I can't install it. 
The documentation says that glipper.autopackage has an  automatic installation (different from glipper.tar.gz - source tarball). But I can't find glipper.autopackage (which extension?), whereas I don't know how to install glipper.tar.gz (I've tried with ./configure and then make, but it doesn't work).

---

### Post by jaboua on 2006-11-19
This really looks interesting, been looking for something like it myself... I'll tell you if I get it installed.
Urukrama, in what repo? Aptitude couldn't find it, so I probably don't have it in my sources.list... I've added all the ubuntuguide ones except backports.

---

### Post by helphope on 2006-11-19
Hi.

I've tried

 sudo apt-get install glipper
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package glipper

---

### Post by Perfect Storm on 2006-11-19
Download the source to your Desktop.

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential gcc-3.4 automake1.7 checkinstall
sudo aptitude install libgnome2-dev libxml-parser-perl gettext libglade2-dev libpango1.0-dev
cd && cd Desktop
tar zxfv glipper-0.95.tar.gz
cd glipper-0.95
./configure
make 
sudo checkinstall

```

---

### Post by jaboua on 2006-11-19
I managed to compile it, works like a dream... Here's a deb:
[http://www.freewebtown.com/jaboua/Ubuntu/glipper_0.95-1_i386.deb](http://www.freewebtown.com/jaboua/Ubuntu/glipper_0.95-1_i386.deb)

I didn't add any dependencies, but in order to compile it I had to install libgnome2-dev, libglade2-dev and libxml-parser-perl - so I guess that in order to run it, you need these two libraries if they aren't allready installed: libxml-parser-perl and libglade2-0

I think the rest of the dependencies should allready be resolved on a normal ubuntu dapper system.

---

### Post by helphope on 2006-11-19
:D :D :D 

Thanks a lot. Glipper works and ... just found what I needed.
If I can still  ask a couple of questions,

1) tar zxfv glipper-0.95.tar.gz is the same as "extract here" (when I click over the file with the right button of the mouse)?

2) Now can I wipe off the glipper-0.95.tar.gz file?

3) Ub....95-1_i386.deb is I guess the autopackage, but how can I find it over there starting from the glipper site?

Thanks everybody

---

### Post by 23meg on 2006-11-19
> **helphope said:**
> 
1) tar zxfv glipper-0.95.tar.gz is the same as "extract here" (when I click over the file with the right button of the mouse)?Yes.
> **helphope said:**
> 
2) Now can I wipe off the glipper-0.95.tar.gz file?Yes.
> **helphope said:**
> 
3) Ub....95-1_i386.deb is I guess the autopackage, but how can I find it over there starting from the glipper site?It's not the autopackage, it's a deb package, the kind of package used by dpkg, the native packaging system of Debian and Ubuntu.

---

### Post by helphope on 2006-11-19
Thanks. Clear and simple.

---

### Post by Perfect Storm on 2006-11-19
If you followed the compile guide I provided you'll find a .deb inside. The .deb file was made with checkinstaller.
The downside of packages made by checkinstaller is that it doesn't solve dependency problem and if you want to install a newer version of glipper you have to uninstall the previous version first. That's why it's not recommended to use other peoples checkinstall packages.
Also when you compiling you're "tailoring" the XXXX application to fits perfectly for your computer and you can change alot of options if you know-how.

---

### Post by mexlinux on 2006-11-19
What you ask for, is default bahaivor in kde

---

### Post by namah on 2006-11-19
> **mexlinux said:**
> What you ask for, is default bahaivor in kde

Yes, klipper has been around for a while but I've always found it a bit unreliable. Hopefully glipper will resolve that and further enhance gnome.

---

