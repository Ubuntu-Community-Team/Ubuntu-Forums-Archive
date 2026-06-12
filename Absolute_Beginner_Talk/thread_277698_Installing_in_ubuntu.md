---
title: "Installing in ubuntu"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by enigmakahn on 2006-10-15
i'll get right out and say this, i know next to nothing about linux, but i know this distro is perfect for my family, cause it will be hard for them to screw up...mostly, anyways, im trying to install the codecs to allow MP3s to play as well as XDiv codec i dl'ed.

anyways, my big question is where do i find the different codecs, and how do i install them

---

### Post by RudolfMDLT on 2006-10-15
Hey! Screwing up a computer is fun! :) It's the only way I learn! ;)

Anyhow! Welcome to the Ubuntu world! I'll try and help where I can!

I read about 3-5 posts a week on people new to Ubuntu not being able to play there media files. The reason you cannot play your files is that they don't come shipped with Ubuntu, the reason being:

> Patent and licensing restrictions on media formats can complicate a free operating system's ability to distribute software that will support those formats. - Quoted from the Ubuntu WIKI

Giving the wiki a read is always a good idea!:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

If you're new to Ubuntu, and you wish for a quick fix, this application is a solution to most of your media troubles! You would really do yourself some good by using Easy Ubuntu:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

It installs all of the codecs you need Plus the Firefox PlugIns for streaming media and the players needed for playing them and a whole lot of other things! It's a real winner!:)

Just one thing, there is a option for installing new graphics drivers. Like the saying goes, if it's not broken don't fix it! If you display works, UNTICK this option. Later when you are more comfortable with Ubuntu and the command line, then go messing around!

If you want to go it with the terminal:

Install the Xine streamer for gnome:
sudo apt-get install gxine

Install all the Windows codecs that you're use to:
sudo apt-get install w32codecs

Then a good media player, Amarok:
sudo apt-get install amarok

For WMV files get Mplayer and all the Mplayer addons for Firefox!

If you have an IPod, you might need:
sudo apt-get install ipodslave

Inorder to play DVD's:
sudo apt-get install libdvdcss2

Hope this helps!

Cheers,

Rudolf

---

### Post by rlozano on 2006-10-15
try this...

$ sudo apt-get install gstreamer0.10-plugins-multiverse \\ 
                 gstreamer0.8-ffmpeg gstreamer0.10-mad gstreamer0.10-plugins \\               gstreamer0.8-lame 

and also this..

 [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/)

hope this helps.... :rolleyes:

---

### Post by nemin on 2006-10-15
> **enigmakahn said:**
> i'll get right out and say this, i know next to nothing about linux, but i know this distro is perfect for my family, cause it will be hard for them to screw up...mostly, anyways, im trying to install the codecs to allow MP3s to play as well as XDiv codec i dl'ed.

anyways, my big question is where do i find the different codecs, and how do i install them
I think this link will help you: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

---

### Post by rlozano on 2006-10-15
sorry, for the correction....

$ sudo apt-get install gstreamer0.10-plugins-multiverse \\
gstreamer0.10-ffmpeg gstreamer0.10-mad gstreamer0.10-plugins \\ gstreamer0.10-lame

---

### Post by bob74 on 2006-10-15
Sorry to but in, but none of these commands are recognised by my installatio.
Any suggestions would be appreciated

---

### Post by sumguy231 on 2006-10-15
Which exact commands (The ones from the wiki?), and where are you typing them?

---

### Post by ReaderRat on 2006-10-15
Download Automatix2 and let it install everything you check (tick).
Automatix Website
          [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by aysiu on 2006-10-15
You don't need to use commands, if you prefer point-and-click:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by n0dl on 2006-10-15
Did you activate all repos by uncommenting the universe and multiverse lines in your sources.list? Then sudo apt-get update && sudo apt-get upgrade
I would take google ubuntu restricted formats or look at the wiki to see what packages you need apt-get. For a media player i suggest mplayer. .avi files (i presume this is what you want to view because you have the divx codec) sometimes contain some win32 encoding in it so make sure to get the w32codec.deb file and install that.

---

