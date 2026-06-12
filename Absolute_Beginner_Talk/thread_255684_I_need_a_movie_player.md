---
title: "I need a movie player"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-09-11
I need a movie player for Ubuntu 6.06 Dapper Drake, the mplayer wont work and I tried getting it to on the commune here and it didnt work so does anyone know a good movie player?

---

### Post by mike3k on 2006-09-11
I like VLC.

---

### Post by Najand on 2006-09-11
Try to install:

```

sudo apt-get install totem totem-xine totem-xine-firefox-plugin libxine-extracodecs gxine gxine-plugin xine-ui

```

It works much better than default totem-gstreamer

---

### Post by Narcoleptic_Insomniac on 2006-09-11
> **Najand said:**
> Try to install:

```

sudo apt-get install totem totem-xine totem-xine-firefox-plugin libxine-extracodecs gxine gxine-plugin xine-ui

```

It works much better than default totem-gstreamer

This is what I get what I typed that in.

"Reading package lists... Done
Building dependency tree... Done
totem is already the newest version.
E: Couldn't find package gxine-plugin"

---

### Post by Narcoleptic_Insomniac on 2006-09-11
I want something that can play WMV format and another one that can play MPG and MPEG formats, one that can do both would be nice to.

---

### Post by Najand on 2006-09-11
If you have it then just install 
```

sudo apt-get install libxine-extracodecs

```
For extra codecs including mpeg, wma and wmv.

---

### Post by old-crusty on 2006-09-11
Try lauching Kaffeine to play your movie.  Totum is the default in Ubuntu 6.06 and it does not work for me either.  I'm watching/listening to Castawy right now in Kaffeine.  It works fine.

---

### Post by grahams on 2006-09-11
xine is powerful, easy to use and can play all the formats. Highly recommended

---

### Post by Najand on 2006-09-11
> **old-crusty said:**
> Try lauching Kaffeine to play your movie.  Totum is the default in Ubuntu 6.06 and it does not work for me either.  I'm watching/listening to Castawy right now in Kaffeine.  It works fine.

Kaffeine is a native KDE package. Totem is nice if it is totem-xine, not totem-gstreamer, which is as you said, the default in Ubuntu 6.06 Dapper Drake.

---

### Post by Narcoleptic_Insomniac on 2006-09-11
So should I just get rid of totem all together because it doesnt work and I just installed kaffeine. Also, whats the purge command again? 
```
 sudo apt-get remove purge totem
``` something like that.

---

### Post by Najand on 2006-09-11
Depends on you, but I don't really recommand people to use KDE natives in Gnome.

---

