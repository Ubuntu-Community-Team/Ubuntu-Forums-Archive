---
title: "Help--error ./configure VLC-0.8.6.c on Ubuntu 7.04"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by bambubambu2 on 2007-10-14
this is the error message:

checking whether build environment is sane...configure:error:newly created file is older than distributed files!
Check your system clock


what should i do for installing VLC media player?
what is wrong?

Any ideea?






thx

---

### Post by Perfect Storm on 2007-10-14
VLC is in synaptic package manager. If it aren't there you need to enable "universe". Can be done in settings tab   ---> repositories. Now reload synaptic and search for VLC.

---

### Post by Ferri on 2007-10-14
The easiest way is to use the version in the repositories:
```
sudo aptitude install vlc
```
You can also use Synaptic if you prefer a GUI. Make sure you have activated universe repositories.

---

### Post by bambubambu2 on 2007-10-14
no, i can't

i don't have internet connection om my ubuntu.

only vlc media player --10 mega downloaded with another computer 

what tipe of erro iS
problem with the gcc compiler ?

solutions?

---

### Post by Perfect Storm on 2007-10-14
Either way, if you want to compile VLC, it require alot of libs/headers/-devs to do so. Check my guide on howto build VLC from source: [http://polarbeardk.blogspot.com/2007/08/build-vlc-from-source.html](http://polarbeardk.blogspot.com/2007/08/build-vlc-from-source.html)

Instead head over at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) download vlc and its dependencies to an USB stick or burn it to a CD/DVD.

---

### Post by bambubambu2 on 2007-10-14
last question : where can i find vlc media player PRECOMPILED ?

ANY IDEEA? I found only the non compiled version.Please help

---

### Post by bambubambu2 on 2007-10-14
last question : where can i find vlc media player PRECOMPILED ?

ANY IDEEA? I found only the non compiled version.Please help



[http://packages.ubuntu.com/feisty/graphics/vlc](http://packages.ubuntu.com/feisty/graphics/vlc)


if i will download this :Source Package: vlc, Download: [dsc] [vlc_0.8.6.release.orig.tar.gz] I WILL HAVE TO BURN IT ON CD ?
IT' ENOUGH?

---

### Post by Perfect Storm on 2007-10-14
It is precompiled, that is the dependency list of VLC. The red dot next to the lib is VLC dependency. Next thing you pick which arch you want to download (amd64, i386, PPC).

---

