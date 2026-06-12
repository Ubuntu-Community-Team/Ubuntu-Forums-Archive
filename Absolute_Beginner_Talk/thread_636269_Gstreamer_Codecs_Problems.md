---
title: "Gstreamer Codecs Problems"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by n0madic on 2007-12-09
I recently threw the newest version of Ubuntu on my PC, but am having trouble playing mp3 and other audio files. I am trying to install the plugins without luck because I have no internet connection to my Ubuntu PC. In other words, I have to download the plugins via a Vista PC and transfer them to Ubuntu via   a usb drive. Any help would be appreciated.

---

### Post by CCNA_student on 2007-12-09
How come your Ubuntu PC has no internet connection? It would be much easier with one. 
If you did you would just type in the terminal:
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot sudo /usr/share/doc/libdvdread3/install-css.sh

   But your Ubuntu computer would need an internet connection. By the way, Totem-GStreamer cannot navigate DVD menu's, you would need Totem-xine or VLC.

---

### Post by n0madic on 2007-12-09
Money is why I don't...lol. I'll work on that but until then a link to a package or something that could be transfered would be prefered.

Thanks though CCNA

---

### Post by CCNA_student on 2007-12-09
DSL from AT&T is only eleven dollars a month(64Kbps upload, 256 download). Do you have that little money. You could borrow a friends internet connection probably, I have before.

---

### Post by Hospadar on 2007-12-09
you can grab any packages you might need (that arn't on the cd) off the [package site]("http://packages.ubuntu.com/gutsy/allpackages").  (it's a big page so be ready to wait) just grab all the packages that start with "gstreamer", for mp3 support, especially the "bad" and "ugly" packages.  you don't really need the packages that end in "doc" or "dbg" these are documentation and debugging packages (repsectively)

It might take a while to resolve dependancies, but if you get errors when installing the packages (you can just double-click them on your ubuntu box to install), look at what dependancies it says you need, go back to the package site and find them.

Also make sure you grab the right packages for your architecture (probably x86, or x86_64 if you are using 64 bit ubuntu), and then save the .deb files you download to a flash drive or cd or whatever.

hope this helps!

---

### Post by CCNA_student on 2007-12-09
Make sure you download Totem-xine and libdvdcss2 if you want to play DVD's. Totem GStreamer cannot navigate menus.

---

### Post by Hospadar on 2007-12-09
> **CCNA_student said:**
> Make sure you download Totem-xine and libdvdcss2 if you want to play DVD's. Totem GStreamer cannot navigate menus.

note that if you use totem-xine (I personally use it, I've had better luck with xine codecs) you'd do pretty much the same thing as above, but get all the xine packages instead of gstreamer (although you may still want the gstreamer packages for some applications)

---

### Post by n0madic on 2007-12-10
Thanks for your help guys, and ill look into that CCNA

---

