---
title: "gim plugins"
date: 2006-03-30
forum: Art &amp; Design
---

### Post by tikal26 on 2006-03-30
Hey want to intall the most recent gimp texturized and resynthisis plugin for the gimp, but I am wondering once I untart it where do you usually put them. What is a good location? I know that I have to ./configure  and make install, but I remember reading about checkinstall that would put it on synaptic. Any one can help me with this?
Thanks

---

### Post by 3rdalbum on 2006-03-31
Checkinstall doesn't put the package into Synaptic, it just compiles it into a .deb package format.

Do a
```
sudo apt-get install checkinstall
```

and then navigate to the directory that contains the sources. Type:
```
sudo checkinstall -D
``` to specify that you want it turned into a Debian package. When the compiling finishes, extract the package in the usual way.

---

### Post by BLTicklemonster on 2006-09-19
I notice that I don't have as many python-fu plugins in ubuntu as I do in windows... 

Can I get them easily in ubuntu using synaptic or terminal? 

Is there a site recommended that has the best that you can find? (which are deb files, not source that needs compiling?)

---

