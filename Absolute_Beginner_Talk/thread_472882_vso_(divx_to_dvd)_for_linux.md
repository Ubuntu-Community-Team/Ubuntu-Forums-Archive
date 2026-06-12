---
title: "vso (divx to dvd) for linux"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by jag1475 on 2007-06-13
[FONT="Comic Sans MS"][SIZE="2"][/SIZE][/FONT]

hi all does any one know if there is a program like vso for linux 

regards
jag1475:popcorn:

---

### Post by wreti on 2007-06-13
Have you tried QDVD Author? It's in the repos.

---

### Post by starcraft.man on 2007-06-13
> **jag1475 said:**
> 

hi all does any one know if there is a program like vso for linux 

regards
jag1475:popcorn:

I see so you have divx files and want to go to DVD format to burn.

I'm gonna take a shot here, I think Devede will do it as long as you have all the codecs installed in Ubuntu (gstreamer and that lot). It converts most formats and puts them into Disk Structure ready to be burned as a DVD. One warning, don't make an ISO with it (its an option in lower left of main screen), there seems to be a small error when making ISO's that sometimes leads to corrupt/unusable images. Always choose the disk structure and burn it like data.

[URL="http://linuxappfinder.com/package/devede"]Devede.
[/URL][URL="http://linuxappfinder.com/multimedia/dvdauthoring"]List of other DVD authoring suites. 
[/URL][Multimedia converters.]("http://linuxappfinder.com/multimedia/videodvdencoders")

Oh and devede is in the repos, you can install it like any other package :

```
sudo aptitude install devede
```

In a terminal.

IF (I don't know, I never converted divx to dvd with it) devede doesn't work check the two other links, an application has certainly already been made to address this. And bookmark linuxappfinder, great site for finding apps.

---

