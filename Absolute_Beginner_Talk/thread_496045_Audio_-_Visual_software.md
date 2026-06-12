---
title: "Audio - Visual software"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-07-08
I have a series of images I want to write to DVD and also to have some music playing in the background. I'm also looking for something that will allow different fade in effects from one image to the next. Anything available like this in Linux please?

---

### Post by rax_m on 2007-07-09
While I don't have any experience in this area.. I'm not sure if Kino ([www.kinodv.org](www.kinodv.org)) will be able to do what you want. 
There's also another one called Cinnerella ..

---

### Post by a.v.l on 2007-07-11
> **rax_m said:**
> While I don't have any experience in this area.. I'm not sure if Kino ([www.kinodv.org](www.kinodv.org)) will be able to do what you want. 
There's also another one called Cinnerella ..

Thanks for trying, but I've just found "DVD Slideshow"   

[http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page) 

which may do exactly what I need.

This can be found in Synapic package manager. Trouble is, after I've installed it, I'm unable to find it on my computer anywhere. Any help to locate it would be apprecated.

---

### Post by sab0403 on 2007-07-11
If it's not on the "applications" menu, try running it by terminal:```
dvd-slideshow
```Using the <TAB> key to autocomplete might help you locate the command.

If you do succeed in running it by terminal, simply create a launcher to it, either to the panel by left-clicking any open part of the panel and then "Add to panel" | "Custom launcher" or to a particular section of the "applications" menu by typing in a terminal:```
sudo gedit /usr/share/applications/<some name for your launcher>.desktop
```and then editing this file (which is the actual launcher) to make it look like this:```
[Desktop Entry]
Name=<whatever you want the launcher to say>
Comment=<whatever appears on the tool tip when you hover over it>
Exec=<the exact command that launches it from terminal, with any options if applicable>
Icon=<location of the icon, apparently only small pngs work... I'm not sure about this though>
StartupNotify=true
Terminal=false
Type=Application
Categories=<Here you'd put Application+whatever category you'd like it in. i.e.: Application;System;>
```

---

