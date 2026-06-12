---
title: "Yet another mplayer plugin question."
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-03
Hi,

It seems that mplayer plugin for my swiftfox doesn't work. I can not see 
videos of these pages.

[http://veratech.aero/flight.html](http://veratech.aero/flight.html)
[http://veratech.aero/asx/Flight%20Control.asx](http://veratech.aero/asx/Flight%20Control.asx)

I used automatix to install swiftfox and swiftfox plugins. I have no problems 
 viewing google video,youtube and so on.

Can anyone help?

Sincerely

---

### Post by Sp00ne on 2006-10-03
I cant get either to work in normal FF.

---

### Post by i-m-p on 2006-10-03
At least I am not alone.

---

### Post by i-m-p on 2006-10-03
Well, I am not sure about why I can not view the pages of the first post.
I can view this video which seems to use same mplayer plugin.
> [http://www.zengakuren.jp/movies/movie_files/060925hosei_movie02.mpg](http://www.zengakuren.jp/movies/movie_files/060925hosei_movie02.mpg)

---

### Post by J0Sb31R on 2006-10-04
I think it's because the totem plugin for firefox overrides some file types (like wmv,..) When i remove it mplayerplug-in plays everyting fine but then i loose the ubuntu-desktop meta from my repository (edgy). Is there a way to override the firefox plugin priority or something? ](*,)

*edit* I "fixed" this by doing

```
sudo chmod 600 /usr/lib/totem/libtotem-*
```

and then i removed my pluginreg.dat file from my .mozilla/firefox folder

Hope this helps anyone :)

---

### Post by lawina on 2006-10-14
> **i-m-p said:**
> Hi,

It seems that mplayer plugin for my swiftfox doesn't work. I can not see 
videos of these pages.

[http://veratech.aero/flight.html](http://veratech.aero/flight.html)
[http://veratech.aero/asx/Flight%20Control.asx](http://veratech.aero/asx/Flight%20Control.asx)

I used automatix to install swiftfox and swiftfox plugins. I have no problems 
 viewing google video,youtube and so on.

Can anyone help?

Sincerely

Works for me in Swiftfox as well as Firefox using mplayer plugin.
Make sure you right click mplayer and change video output to X11.

---

### Post by i-m-p on 2006-10-14
I've Re-installed my system and this time I used Automatix2 to install those plugins,codecs and so on as much as possible. It works now.

However Acrobad Reader never works! It never run from Application>Office>Acrobat.

---

