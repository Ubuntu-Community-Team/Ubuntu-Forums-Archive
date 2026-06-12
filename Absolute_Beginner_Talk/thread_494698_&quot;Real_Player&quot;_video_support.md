---
title: "&quot;Real Player&quot; video support?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by calymea on 2007-07-07
Hi, I have "Totem" installed and working for video playback. What I would like to know is, what do I have to do to  play back "Real Player" videos, and can I do it without ruining my current DVD playback? Some stuff I want is only available in "Real Player" or "Windows Media Player". If there was a way to get that going, that would be great too. Thanks everyone.

---

### Post by robertc36 on 2007-07-07
You can install both of those quite easily have a search around the forum

---

### Post by omkarwagh on 2007-07-07
which format are you talking about?
ive found that totem is lacking in playing a lot of formats.
try vlc media player(also there in synaptic)
it can run most of your video formats. notable exceptions being .wmv

---

### Post by Old Pink on 2007-07-07
[http://uk.real.com/player/select/](http://uk.real.com/player/select/)

There's a realplayer for Linux right there, just download it somewhere memorable. (e.g Desktop)

Right click it, head to properties and make sure "Allow executing file as a program" is ticked.

Go into terminal, and type:```
sudo /location/of/file/file.bin
``` to install the .bin file. :) 

You must use sudo, otherwise it doesn't install firefox plugins correctly. :D

---

### Post by calymea on 2007-07-11
hi mate, downloaded the bin. file, followed your instructions to the letter and, got the message; "no such file or directory". Could you help some more please? P.S. I downloaded it to "desktop".

---

### Post by Hallvor on 2007-07-11
> **omkarwagh said:**
> 
try vlc media player(also there in synaptic)
it can run most of your video formats. notable exceptions being .wmv

VLC plays .wmv just fine. It will not play .rm.

---

### Post by RomeReactor on 2007-07-11
Hi. **calymea**, try this from the terminal:
```
cd Desktop
```
and
```
sudo ./RealPlayer10GOLD.bin
```

---

### Post by mr_biggie on 2007-07-11
you dont need to install real player you can play real media and wma/wmv in totem with out a problem just look for the gstreamer plugins in synaptic. you can also just install automatix2 it will makes things alot easier

---

### Post by calymea on 2007-07-12
> **RomeReactor said:**
> Hi. **calymea**, try this from the terminal:
```
cd Desktop
```
and
```
sudo ./RealPlayer10GOLD.bin
```

hi Rome Reactor, thanks for trying to help, but I still get "no such file or directory" even doing it the you said.
Any other ideas?

---

### Post by RomeReactor on 2007-07-12
Did you copy/paste the commands? Remember that commands are case sensitive, so **desktop** is not the same as **Desktop**. Also, is **RealPlayer10GOLD.bin** your file's name?

---

### Post by calymea on 2007-07-12
Thanks Rome Reactor, it worked this time! Anything else I have to do to set it up before I can use it?

---

