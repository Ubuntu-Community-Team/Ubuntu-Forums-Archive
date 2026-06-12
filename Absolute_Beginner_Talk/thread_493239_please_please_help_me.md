---
title: "please please help me"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by arif9k on 2007-07-05
i donot have an internet connection

---

### Post by Majorix on 2007-07-05
Arif, you could just use the Synaptic tool to install software much easier. There you can search for a media player to your like, and install it with a single click. If you need an advice on which to choose, I can recommend xmms, which I use too.

And next time please choose titles to your threads more carefully. "Please please help me" doesn't tell anything about the contents of your post.

---

### Post by greg_g on 2007-07-05
If your main goal is to play mp3s a good place to start is this page, it will tell you everything you need to know:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good luck,

greg

---

### Post by annda on 2007-07-05
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

you can bookmark the guide for all later questions, too.

and beep is in the repositories. you can use synaptic
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_apt-get_the_easy_way_.28Synaptic.29)

---

### Post by Cypher on 2007-07-05
Never heard of Beep-media-player. There is XMMS on Linux, an awesome Winamp clone that you can install. There are also a bunch of other full-feldged MP3 players like Rythmbox, Banshee and so on..

Always use APT-GET or SYNAPTIC to install packages whenever possible..

---

### Post by moore.bryan on 2007-07-05
[I]i would suggest not going with bmp, but it's next-generation version, audacious.
```
sudo aptitude install audacious
```for the media codecs, go with what is on the [ubuntuguide.org]("http://www.ubuntuguide.org/") site:
[/I]> ** How to install Multimedia Codecs **
[LIST]
[*]Read [#General Notes]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#General_Notes")
[*]Read [#How to add extra repositories]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")[/LIST]```
sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```*The "ubuntu-restricted-extras" is a meta-package that installs : flashplugin-nonfree, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, msttcorefonts,sun-java6-jre and sun-java6-plugin* [I]Important note: that w32codecs are copyright infrigement since they are basically exact copies of DLLs that are shipped by various Windows software to handle media formats.
[/I]

---

### Post by misfitpierce on 2007-07-05
There is beep media player for linux... google it and I think it may come in automatix

---

