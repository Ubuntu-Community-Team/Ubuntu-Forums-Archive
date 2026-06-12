---
title: "Ubuntu's Sound of Silence"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-09-17
Hello, I just noticed that Ubuntu is too silent or there's no much sound/sfx/sound scheme going on. I only heard sound when login,logoff, errors, some clicks.... there's no sound even in browsing like when clicking on the links. I tried to play Runescape(dont have any installable games yet... ehehe) but I dont hear any sound, BG sound or sound effects. 

I can play audio/video files without any problem.

---

### Post by poofyhairguy on 2005-09-17
[QUOTE=jeffreyvergara.NET]Hello, I just noticed that Ubuntu is too silent or there's no much sound/sfx/sound scheme going on. I only heard sound when login,logoff, errors, some clicks.... there's no sound even in browsing like when clicking on the links. I tried to play Runescape(dont have any installable games yet... ehehe) but I dont hear any sound, BG sound or sound effects. 

I can play audio/video files without any problem.[/QUOTE]

This is a bug that will be fixed in Breezy. Its the biggest problem in Hoary. To kinda fix it, run this command in the "run program" thing when you want sound from browser and such:

> killall esd

then if you want other sounds back put in this:
> 
esd

ESD- Enlighted Sound Daemon. Its fixed in Breezy, so when thats released in a month it will all be better.

---

### Post by jeffreyvergara.NET on 2005-09-18
thanks for the info, I think i'll just wait for Breezy.. ehehe

---

