---
title: "A music player that can handle MP3 files?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by KeriaII on 2006-03-08
I'm using Ubuntu and finding it very good, but neither of the players I have ( Totem and Rhythm Box) will play MP3 files: a bit of a pain as most music files come in this format now.

Does anyone know of any alternative players I could use and if so, how to procure them?

---

### Post by Brunellus on 2006-03-08
please consult the RestrictedFormats page on the wiki for help on getting the MP3 codecs.  Or search these forums for Automatix.

---

### Post by jocko on 2006-03-08
beep-media-player (bmp) plays mp3 out of the box. Just enable the universe  repositories and:
Run these commands from a terminal:
```
sudo apt-get update
sudo apt-get install beep-media-player
```
Or search for it in synaptic and install it from there...

Edit: Didn't see I was in the "Absolute beginner" section... 
This is how to enable universe:
```
sudo gedit /etc/apt/sources.list
```
Find a section in the file looking like this:
[COLOR="Red"]
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse[/COLOR]

remove the "# " before the two lines, save and close the file.

---

### Post by aysiu on 2006-03-08
It's not the players; it's the codecs.
You need the lame codecs to be able to play MP3s.
See the aforementioned Restricted Formats page.

---

### Post by %hMa@?b&lt;C on 2006-03-08
get automatix, install the NON-Free Codecs; that are punishable by law <lol>:KS

---

