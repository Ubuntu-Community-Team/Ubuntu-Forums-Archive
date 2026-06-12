---
title: "burning .cue image og .mp3 file"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-03-24
Im wondering how i can burn a .cue image of an .mp3 file?
I have a music file that name.mp3 and a name.cue file and i want to burn this but i cant do it at all. iv tryed with k3b but that dont work and iv tried with cdemu to mount but that just fails.

---

### Post by annda on 2007-03-24
i don't think this can be done that easily, because the cuesheet in ths case describes an mp3 file, not an image file.

to the best of my knowledge, you will have to split the file first. you can use mp3splt or mp3cue (included in poc-streamer). both are in the repositories.

---

### Post by U5tabil on 2007-03-24
ok.

installed mp3splt but i dont know how this works, i need to look for an HOWTO if you dont know of one that is.

---

### Post by annda on 2007-03-24
official man page (look for the -c option):
[http://mp3splt.sourceforge.net/mp3splt_page/documentation/man.html](http://mp3splt.sourceforge.net/mp3splt_page/documentation/man.html)

there is also a gui - mp3-splt-gtk - not in the repositories, but as a .deb package (download, double-click to install). i haven't tested it yet:
[http://mp3splt.sourceforge.net/mp3splt_page/downloads.php](http://mp3splt.sourceforge.net/mp3splt_page/downloads.php)

ps. for most command-line programs you can get the options by typing

```
man name_of_program
```

or

```
name_of_program --help
```

i know, i don't like how complicated the info is either, but most of the times you will get what you need.

---

### Post by Jose Catre-Vandis on 2008-06-13
K3b will do this (Hardy)

go into synaptic, install libk3b2-extracodecs, then in k3b choose Burn cd image, select the cue file and away you go :)

---

