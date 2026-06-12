---
title: "MP3 Player"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by jomon_johnson on 2006-12-29
I installed ubuntu smootly and liked very much.But i cannot play mp3 files.I downloaded **Xine** and xinelib.But i cannot install.The problem is that their is no c compiler.can u suggest a good mp3 player which does't need compilation.also please say how to install c compilers
With Respect
Jomon Johnson
:(

---

### Post by 23meg on 2006-12-29
You most likely don't need to compile anything. In these sites you'll find the basics on how to install software:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To play mp3 files, you'll need to install a codec. See here:

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by johnnymac on 2006-12-29
First - you may want to look into using automatix.  The guys who put it together did an AWESOME job at making some of the irritating issues of Ubuntu|Linux "go away"

[http://www.getautomatix.com/](http://www.getautomatix.com/)

But...you can always do things the long way.  To install compilers and such needed to build things you need to do the following from a terminal:

```

sudo apt-get install build-essential

```

---

### Post by obsidion on 2006-12-29
> **jomon_johnson said:**
> I installed ubuntu smootly and liked very much.But i cannot play mp3 files.I downloaded **Xine** and xinelib.But i cannot install.The problem is that their is no c compiler.can u suggest a good mp3 player which does't need compilation.also please say how to install c compilers
With Respect
Jomon Johnson
:(


  sudo apt-get install xmms xmms-mad

Simple straight foreward player. If you use synaptic just do a search for xmms and install the things you might want, like skins etc.

---

### Post by Some_Person on 2006-12-29
You can use Rhythmbox. Just install the gstreamer0.10 plugins in Synaptic.

---

### Post by AndyCooll on 2006-12-29
> **23meg said:**
> To play mp3 files, you'll need to install a codec. See here:

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

As mentioned, these are the only instructions you need to get mp3  files to play (it's also in my signature).

:cool:

---

### Post by TooRight on 2006-12-29
I just install the codecs I need through Automatix2 and then use Amarok to play my mp3's

---

