---
title: "Playing a DVD"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by zappa86 on 2005-07-31
I have the ubuntu amd64 version installed and I want to play DVDs. So I dl some software and do the './configure' script. And it says I dont have a compiler. So after some searching I install the build-essential (apt-get install build-essential). Now when I do the configure it says it cant find the libxext library. So I'm asking for you help:

Anyone know a DVD player that I can get and install easly.
-and/or-
Does anyone know what to do abnout the libxext?

Thanks

---

### Post by codejunkie on 2005-07-31
[QUOTE=zappa86]I have the ubuntu amd64 version installed and I want to play DVDs. So I dl some software and do the './configure' script. And it says I dont have a compiler. So after some searching I install the build-essential (apt-get install build-essential). Now when I do the configure it says it cant find the libxext library. So I'm asking for you help:

Anyone know a DVD player that I can get and install easly.
-and/or-
Does anyone know what to do abnout the libxext?

Thanks[/QUOTE]
totem-xine, mplayer, xine-ui all of these can be installed thru synaptic they all work well but you will have to install some other things to play dvd and other protected formats [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) will help you with that.

---

### Post by bored2k on 2005-07-31
[QUOTE=codejunkie]totem-xine, mplayer, xine-ui all of these can be installed thru synaptic they all work well but you will have to install some other things to play dvd and other protected formats [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) will help you with that.[/QUOTE]
 Installing libdvdcss2 is more vital than any of the packages you mentioned.

---

### Post by zappa86 on 2005-07-31
what is synaptic and how can I install it. (Ive been using linux for 6hours now so I'm a complete n00b). Thanks.

---

### Post by heimo on 2005-07-31
System->Administration->Synaptic Package Manager

---

### Post by codejunkie on 2005-07-31
[QUOTE=bored2k]Installing libdvdcss2 is more vital than any of the packages you mentioned.[/QUOTE]
true but that's why i gave that link to ubuntuguide it covers installing libdvdcss2 and the other codecs as well, but i should have mentioned that it was more important for dvd playback.

---

### Post by zappa86 on 2005-07-31
[QUOTE=heimo]System->Administration->Synaptic Package Manager[/QUOTE]

Its not there for me. I'm running the AMD64 verson. Perhaps I need to install something before that? I'm in dependancy hell.

---

### Post by codejunkie on 2005-07-31
[QUOTE=zappa86]Its not there for me. I'm running the AMD64 verson. Perhaps I need to install something before that? I'm in dependancy hell.[/QUOTE]
if you cant find synaptic there press ctrl+alt+F2 and enter ```
gksudo synaptic
```it will ask for a password enter your password and it will open synaptic.
edit: if that still doesn't open synaptic open a terminal and do 
```
sudo apt-get update
``` 
```
sudo apt-get install synaptic
```
```
killall gnome-panel
```
this will reinstall synaptic if something went wrong during your install.

---

### Post by zappa86 on 2005-07-31
I installed libdvdcss2 and I see it as installed in synapatic. However, whenever I try to play a DVD with xine it wont work. is there configuration that must be done. Thanks

---

