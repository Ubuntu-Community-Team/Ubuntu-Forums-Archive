---
title: "copying dvds"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-04-12
what is the best program to use to rip dvds also what is the best program to use to make avi's etc to dvd?

---

### Post by gerbman on 2006-04-12
[QUOTE=ice.man]what is the best program to use to rip dvds also what is the best program to use to make avi's etc to dvd?[/QUOTE]Try the dvdrip package for ripping dvds. Works great for me.

---

### Post by trent dillman on 2006-04-12
I'm not sure about ripping, but I've seen dvd::rip and acidrip...

...avi to dvd, that's a bit easier. Convert the avi to DVD mpeg using either transcode or ffmpeg (I think you can use the GUI app Avidemux for this?), then author with dvdauthor (there's a GUI called qdvdauthor, and there's DVDStyler as well)...

I have a script on my other box that converts avi to DVD mpg2. I'm going to have to set it up sometime....

---

### Post by frodon on 2006-04-12
dvdrip, avidemux or DVDshrink with wine.

---

### Post by ice.man on 2006-04-12
does that didrip burn as well???????

---

### Post by gerbman on 2006-04-12
[QUOTE=ice.man]does that didrip burn as well???????[/QUOTE]Yup. Requires a little configuring, but nothing too difficult.

---

### Post by ice.man on 2006-04-12
like?

---

### Post by StefanoCole on 2006-04-12
There is also xdvdshrink, and you can burn with it.

Stefano

---

### Post by Mustard on 2006-04-12
[QUOTE=ice.man]like?[/QUOTE]

..like the instructions on the website. :)

[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)
[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

---

### Post by nalmeth on 2006-04-12
acidrip always worked best for my dvd ripping.
In the repos under the same name

---

### Post by ice.man on 2006-04-12
thanx guys but i have one more thing i ripped some dvds when i had windows 
and there in folders called audio_ts and video_ts how would i burn them off onto dvds now?

---

### Post by trent dillman on 2006-04-12
You could use K3B...just start a new DVD Video, and drop those folders in the root layout. Also, you could use mkisofs (CLI)...

EDIT: You might test them with xine

```
xine dvd:/path/to/dvd
```

---

