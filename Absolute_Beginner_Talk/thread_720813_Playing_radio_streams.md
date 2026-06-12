---
title: "Playing radio streams"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by jano_rajmond on 2008-03-10
Can anyone tell me a good program (package name and extra plug-ins needed) in order to play back radio stream like: [http://radio.server.ext/](http://radio.server.ext/) or [http://ip.add.re.ss: port](http://ip.add.re.ss: port).

RealPlayer, RhythmBox Music Player and XMMS all give unsupported file type error.

Thanks very much!

---

### Post by Bubba64 on 2008-03-10
Your address leads to no where I have every addon  plugin and codec so I know it's not my computer.

---

### Post by kostkon on 2008-03-10
It depends of what format is the streaming media. First of all, install the *ubuntu-restricted-extras* package from *Add/Remove* or S*ynaptic*. Then, add the [*Medibuntu* repository]("http://medibuntu.org/") to your software sources list. Instructions on how to do it you can find [here]("https://help.ubuntu.com/community/Medibuntu"). After adding this repository, install the *w32codecs* package from *Synaptic* or by opening a terminal and doing
```
sudo apt-get install w32codecs
```
Also, install the *gstreamer0.10-pitfdll* package (if it has not been already installed) from *Synaptic* or terminal, doing
```
sudo apt-get install gstreamer0.10-pitfdll
```

After that, try again to play your stream using *Totem* or *Rhythmbox*.

Other good media players you could install are: *Mplayer* and *VLC*.

---

### Post by jano_rajmond on 2008-03-10
You and VLC rule ;)

I already knew that VLC is a pretty decent media player, but now I think it's great :D

RhythmBox, XMMS and RealPlayer still cannot play the streams (unknown file type) but VLC handles them all great.

P.S.: The streams broadcast ogg, acc and mp3

Thank you very much for your help!

---

### Post by jano_rajmond on 2008-03-10
> **Bubba64 said:**
> Your address leads to no where I have every addon  plugin and codec so I know it's not my computer.

I know that the addresses lead nowhere... doooh... they were just an example so you can see what type of urls I am talking about.

---

### Post by jano_rajmond on 2008-03-11
I found another solution for the problem which only entered my mind just now (although Linux enthusists will NOT like this :P)

```
sudo apt-get install wine

cd /media/hda1/Program\ Files/Winamp/

wine winamp.exe
```

:D

---

