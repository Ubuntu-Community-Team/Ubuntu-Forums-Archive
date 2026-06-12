---
title: "Compiling ffmpeg on Ubuntu"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by sa125 on 2008-01-20
Hi - I'm trying to use Floola to manage my ipod video under ubuntu, and I read on Floola's doc page that:
> # FFmpeg executable has to be installed under /usr/local/bin. It has to be manually compiled with at least aac and h264 plugins.


This allows the user to drag & drop files into the application to convert them for ipod use, and avoid interacting with command line encoders. Being really new to linux, my question is - how do I do that?... Thanks!

---

### Post by AlexenderReez on 2008-01-20
i think you can get ffmpeg from medibuntu
> [http://medibuntu.org/](http://medibuntu.org/)

for manual,this should help...
> [http://tuxrip.free.fr/installation_en.html](http://tuxrip.free.fr/installation_en.html)

i dont really sure about this-->

> [http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml](http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml)

---

### Post by jleaker01z on 2008-01-20
ffmpeg can be installed via synaptic (System>Administration>Synaptic package manager)

Search for ffmpeg and you will see it.  But Im not sure that will do what you need, as far as those 2 plugins go.  But it may be worth a shot...alot easier than trying to compile and install it manually.

---

### Post by yabbadabbadont on 2008-01-20
If, for some reason, you need the latest and greatest version, you can try to follow these instructions:

[http://tovid.wikia.com/wiki/Installing_svn_ffmpeg_on_a_Debian_based_distro](http://tovid.wikia.com/wiki/Installing_svn_ffmpeg_on_a_Debian_based_distro)

Edit: I wouldn't use the debian repositories like it says though.  I would stick with the Ubuntu ones, or maybe the mediabuntu ones listed by the previous poster.

---

### Post by mjpatey on 2008-01-20
As yabbadabbadont said, you can install the latest and greatest... but the version in the repositories should be just fine, assuming it includes the aac and h.264 plugins.

---

