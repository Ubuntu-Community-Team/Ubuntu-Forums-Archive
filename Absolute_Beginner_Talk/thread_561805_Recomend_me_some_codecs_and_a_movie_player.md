---
title: "Recomend me some codecs and a movie player"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by _d5 on 2007-09-28
Hi,

I have not installed any additional codecs or any players and i experience some problems with the watching of movies, viewing Cirilyc subtitles and with some music formats.

Please recomend me some codecs and players!

Thank you!

---

### Post by swisscow on 2007-09-28
VLC plays almost everything

As for codecs, try the ubuntu restricted extras package

Or follow the sticky at the top of the absolute beginners forum

---

### Post by lgcabarcas on 2007-09-28
you could also try with Mplayer install the Gstreamer codec packages and you'll be ready to go, if you experience any problem try to enter the preferences dialog and choose from the avaiable video drivers, the **gl** one worked for me :popcorn:

---

### Post by _d5 on 2007-09-28
> **swisscow said:**
> VLC plays almost everything

As for codecs, try the ubuntu restricted extras package

Or follow the sticky at the top of the absolute beginners forum

I read the Sticky thread, but i have problems with the Restricted section and the Flash player....

I have a problem with the last section of the sticky thread, i added the new sources, but i can not save the file, which i have edited with the text editor, so i could not continue...

---

### Post by _d5 on 2007-09-28
> **lgcabarcas said:**
> you could also try with Mplayer install the Gstreamer codec packages and you'll be ready to go, if you experience any problem try to enter the preferences dialog and choose from the avaiable video drivers, the **gl** one worked for me :popcorn:

I typed gstreamer in Synaptic and marked everything for installation, now I am waiting so later i will install mplayer and will give you the result.

Mplayer crashes with a Fatal error!

Any ideas?!

---

### Post by lgcabarcas on 2007-09-29
mmm... the problem with the text editor, are you using sudo along with the text editor command? that may be the reason you can't the file

---

### Post by meborc on 2007-09-29
you have to edit the sources list file as root... for example ```
gksudo gedit /etc/apt/sources.list
```

---

