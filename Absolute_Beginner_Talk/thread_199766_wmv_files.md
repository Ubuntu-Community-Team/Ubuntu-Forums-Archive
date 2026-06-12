---
title: "wmv files"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-19
I've downloaded and installed the codecs 
and I've done everything that you said - but I still unable to play thouse files
it is very important
please help

---

### Post by FredB on 2006-06-19
Which player are you using ? Mplayer and Xine works both great with DRM-free wmv videos.

---

### Post by MaximB on 2006-06-19
DRM-free ???
what is it ???
I'me using Mplayer

---

### Post by FredB on 2006-06-19
DRM-free = without DRM (Digital Right Management). Sorry for not being clear.

[http://en.wikipedia.org/wiki/Digital_Rights_Management]("http://en.wikipedia.org/wiki/Digital_Rights_Management")

How did you install your codecs ?

---

### Post by MaximB on 2006-06-19
add/remove - installed some codec packages
and then run some long commands that were given to me at the forum

---

### Post by Jagot on 2006-06-19
Follow this guide:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by MaximB on 2006-06-19
I've manages to run thouse files with Mplayer
but why can't I run them on totem ?

---

### Post by Jagot on 2006-06-19
If you've installed the codecs from the repos suggested by the restricted formats wiki page and you have installed w32codecs then it should be working.  The only thing I can suggest is to run through it again.

---

### Post by MaximB on 2006-06-19
the problem is that in this wiki there is a command that supposed to install a codec file "w32codecs...deb" and the file does not exist.
I'm tring to download it from amule
but it's damn ssllooww...
much slower then emule...

is there another link to this file ?
or a way to make amule to run faster ? or maybe use other program ???

---

### Post by Jagot on 2006-06-19
If you add this line to your sources.list and then you can install from Synaptic of apt-get/aptitude install it:

```
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
```

---

### Post by MaximB on 2006-06-19
thanx very much

---

### Post by MaximB on 2006-06-19
well I've reinstalled the deb package and still only the Mplayer can run it.
but when I pause the file it cannot be resumed only restarted.

---

### Post by FredB on 2006-06-19
[QUOTE=MAXDDARK]well I've reinstalled the deb package and still only the Mplayer can run it.
but when I pause the file it cannot be resumed only restarted.[/QUOTE]

Mplayer support for WMV files is random. But at least, your computer can read them ! :D

---

