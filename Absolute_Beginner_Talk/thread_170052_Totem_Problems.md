---
title: "Totem Problems"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-03
Totem will not play my DVD's. I tried several and it gives me this error:  **Only a subtitle stream was detected; either you are loading a subtitle file, or the media file was not recognized, which means you may need to install additional plugins**  What plugins is it talking about?  Do I have run updates for Totem?:confused:

---

### Post by nanotube on 2006-05-03
have you installed dvd playback libraries, or is this "default" totem that you got with the install?
at any rate, you will have better luck playing stuff with totem-xine, so run
```
sudo apt-get install totem-xine
```
from the terminal to replace default totem with totem-xine.
or you could try mplayer instead.
at any rate, check out 
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
for more info about playback of various media.

---

### Post by NeoGreen on 2006-05-07
I'll try it thanks:D

---

### Post by NeoGreen on 2006-05-07
Ha, it worked thanks:-({|= :D

---

### Post by nanotube on 2006-05-07
great. have fun! :)

---

