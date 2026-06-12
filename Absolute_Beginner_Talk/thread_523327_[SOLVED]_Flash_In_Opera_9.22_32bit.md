---
title: "[SOLVED] Flash In Opera 9.22 32bit"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-08-11
I was wondering how to get flash working in Opera 9.22.  I found a guide for 64bit, but not 32bit.  I'm sure there is one, but can someone point me in the right direction, because I couldn't find it.  Thanks.

---

### Post by riven0 on 2007-08-11
If you have the flash plugin for Firefox installed, then all you have to do is open up Opera and go to: Tools >> Preferences >> Advanced >> Content >> Change Path. And then just add this location: /usr/lib/firefox/plugins

Then restart Opera, and flash should be recognized.

---

### Post by Specter043 on 2007-08-11
I have flash in firefox, and I added that in Opera, but it still doesn't work.  maybe my firefox flash is in a different location.

---

### Post by Specter043 on 2007-08-11
Maybe I could move my Flash install there?  Does anyone have any other ideas where Flash would be located?

---

### Post by Damiel on 2007-08-11
The flash plugin files are here in my system: /usr/lib/flashplugin-nonfree

---

### Post by Specter043 on 2007-08-11
Flash on opera hates me, my flash isnt there either.

---

### Post by riven0 on 2007-08-11
> **Specter043 said:**
> Flash on opera hates me, my flash isnt there either.

This may sound stupid, but after you did the Change Path thing, did you click on Find New to search for the plugins and then restart Opera?

---

### Post by Specter043 on 2007-08-11
errrr....let me try that.

---

### Post by Specter043 on 2007-08-11
No, flash didnt show up

---

### Post by RomeReactor on 2007-08-11
Hi. Please run this command in the terminal (Applications->Accessories->Terminal):
```
locate libflashplayer.so
```
and post the results.

---

### Post by Specter043 on 2007-08-12
I did the command and added it.  it was in /home/specter/.mozilla/plugins/libflashplayer.so
.  Well thanks for the help.

---

