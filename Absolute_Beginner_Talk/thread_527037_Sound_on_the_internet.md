---
title: "Sound on the internet"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by natman on 2007-08-16
I have feisty and sound works fine in amarok and stuff, but you tube and other internet stuff with sound never plays the sound, ie on you tube i see the video but no sound? is there a way to ix this?

---

### Post by atihimself on 2007-08-16
seems, that you missing some codecs, if you use automatix its easy to find and install the right ones

---

### Post by Arthur Archnix on 2007-08-16
Before trying automatix, be sure to learn a little more about it. If you do so you'll eventually come across an article explaining how the ubuntu team looked at the program and came to the conclusion that it was poorly written and could possibly break systems.

Start with this command, and then, if it still doesn't work, post back here or go take a look at the [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins").

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Bofur on 2007-08-16
I had a similar problem to yours awhile back. Try using this command:
```
sudo apt-get install vlc-plugin-* mozilla-plugin-vlc

```
This will install the vlc plugins for firefox and should allow you to play just about anything. Another thing is to make sure you have the latest version of flash installed.

---

### Post by natman on 2007-08-18
I tryied installing the vlc plugin and the restricted repos things, neither worked. Actually the seemed to mess up my sound, but i as able to recover it again. I had a lot of trouble getting ALSA working on my laptop using this guide
[HTML]http://ubuntuforums.org/showthread.php?t=455147&highlight=dv2000+hp[/HTML]
any more ideas?

---

