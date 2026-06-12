---
title: "WINE still won't work"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2006-01-25
Originally, I was going to install wine 0.9.6 from source. When I tried to run it though, it gave me a library related error and I decided it would be easier to install through apt. Unfortunatly, I seems that make uninstall did not completly remove all traces of wine. When I try to run wine from the default shell, it references to /usr/local/bin/wine and can't find it. The only way I can get it to run is by manually typing the directory path. Also, winecfg crashes upon clicking the audio tab, and wine won't even start GTA:VC, a game that I had gotten running earlier on another version of wine.

I've tried to sudo make uninstall from the dir of wine source, and I've run dpkg --purge wine multiple times but to no avail. How do I fix this?

---

### Post by wr0x2 on 2006-01-25
All right, the path for wine seems to be set correctly now, but winecfg still crashes on the audio page and wine still won't run my app.

What's going on here?

---

### Post by n8ey on 2006-02-08
Old post to comment to, but I found a partial answer for this.

I had the winecfg crashing problem when going to the Audio tab, until I found my sound module wasn't loaded and ALSA compatible.

I mod-probed the correct one and it doesn't crash now.

The not-launching your program I'm not to sure about.  What program is it and are you using wine or Windows libraries?

---

### Post by n8ey on 2006-02-08
It would be cool if I could read better...  ;)

The program you're running, GTA:VC might need Cedega installed for DirectX to be usable.

---

