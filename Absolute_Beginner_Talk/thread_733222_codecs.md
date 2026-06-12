---
title: "codecs ???"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by saurabhgupta on 2008-03-23
hi 
i am new to ubuntu and i have installed it for the first time...
i cant play any songs and videos(mp3/mpg).
neither can i execute the exe file. my intention was to connect 
the internet and download the codecs.
But right now i can't even connect the net.
Any suggestion thru which i can get the codecs  etc... and 
start using windows exe and songs...


i have tried installing wine but it states to enable a component "universe" 
:( Help plz...:(

---

### Post by Sh@m@n on 2008-03-23
If you have Ubuntu 7.10 or higher, try

```
sudo apt-get install ubuntu-restricted-extras
```

from terminal.

---

### Post by Darganot on 2008-03-23
System -> Administration -> Network

Make sure you have your ip set here if you're behind a router.  Make sure your DNS and all other information about your connection is entered here and correct.

---

### Post by billgoldberg on 2008-03-23
.exe won't work (those are windows installers)

to install software go to:

applications -> add/remove  or  system -> administration -> synaptic package manager

---

### Post by fela on 2008-03-23
to enable universe repos, goto System > Admin > Software Sources, select the universe repository.

But you can find all the codecs natively for Linux (don't need those .exe files, they're windoze apps) if you goto System > Admin > Synaptic, search for 'gstreamer' (w/o quotes) and mark all the gstreamer codecs for installation. Then click apply, wait for it to finish.

Enjoy the music...

---

