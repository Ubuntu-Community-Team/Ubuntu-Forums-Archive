---
title: "Offline installation of VLC player"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-10
I tried to install VLC media player while offline.

sudo dpkg -i vlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb

However, the installation was not completed, as I was missing the following packages:

	libdvbpsi3
	libmodplug0c2
	libmpeg2-4
	libtar
	wxvlc

So I manually installed them. However, wxvlc could not be installed, because 

1)package libwxgtk2.4-1 was not installed
2)**package VLC was not configured.**

I installed package libwxgtk2.4-1, but wxvlc still refuses to install because "VLC is not configured". Of course, I cannot configure VLC, because in order to install it, I need wxvlc. So I'm spinning around my tail. What could I do?

Please don't tell me to use synaptic or apt-get because the Ubuntu machine is permanently offiline.

---

### Post by macdo on 2006-04-17
Try to reinstall vlc at the same time. They do indeed depend on each other.
So try ```
dpkg -i wxvlc-blabla.deb vlc-blabla.deb
```
If that doesn't work, you can actually make a local apt repositoory that should solve your problem. Read the Apt Howto at [http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html) - the bit you want is at [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

---

