---
title: "mp4 in amarok?"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by theinvictus on 2005-09-09
Hey, I've been toying around with the various media players for ubuntu, and I was using rhythmbox and downloaded the appropriate downloads so that it would recognize all my files from iTunes....however when I tried amarok I was blown away by it and decided to switch to amarok, however when I import my audio files with it, I only get half my library...is there anything I can download to make amarok get the rest of my files?

---

### Post by manicka on 2005-09-09
Use the gstreamer engine with amarok and install the gstreamer plugins meta package

---

### Post by theinvictus on 2005-09-11
where do I get the meta package....in synaptic all I see as far as gstreamer-plugins
is 0.8-0 and 0.8-0-dev

---

### Post by manicka on 2005-09-11
[QUOTE=theinvictus]where do I get the meta package....in synaptic all I see as far as gstreamer-plugins
is 0.8-0 and 0.8-0-dev[/QUOTE]
 Enable the universe repo to access these extra plugins

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by theinvictus on 2005-09-11
Alrite, nevermind, I realized I had that installed already....amarok is still only finding about 2,600 of my over 4,200 songs....songs that Rhythmbox is able to find perfectly fine....

---

### Post by manicka on 2005-09-11
[QUOTE=theinvictus]Alrite, nevermind, I realized I had that installed already....amarok is still only finding about 2,600 of my over 4,200 songs....songs that Rhythmbox is able to find perfectly fine....[/QUOTE]
 Did you refresh apt?

sudo apt-get update

the package you are looking for is gstreamer0.8-plugins

this is a meta package that will install all the available plugins for gstreamer

---

### Post by theinvictus on 2005-09-13
yeah I installed the plugins, but it still doesn't find the extra songs

---

