---
title: "MP3 won't play"
date: 2006-03-09
forum: Apple PPC Users
---

### Post by sarcasticfrench on 2006-03-09
I'm running Kubuntu  on an iBook g3 300 mhz. Pretty much everything is working, except I just can't play MP3's in amarok. I can play them in Juk, but since Juk can't play anything over Samba shares it is pretty much worthless as I just don't have the HD space to copy all my music over from my PC. When I start up amarok, and open the mp3 file over the Samba share, it says its playing but it just sits there doing nothing. I installed the gstreamer and akobe-mpeg packages, but it still doesn't work. Does anyone know how to fix this? I'm fine with installing a different application or whatever, I just want to be able to play my MP3's through a Samba share. Thanks!!


**Update: I installed the xine-totem package, and that can play music over Samba shares. **

---

### Post by maple on 2006-03-09
Have you installed the gstreamer mp3 plugin? I don't think that Juk uses gstreamer so maybe thats why it is working. Give it a shot.

---

### Post by sarcasticfrench on 2006-03-09
Yes, I did install the gstreamer plugin for amarok. I also updated it, as the version that came with Kubuntu was not the newest.

---

### Post by jasongamer14 on 2006-08-15
](*,) grrr iv updated everything iv look for everything on iternet i CANT find how to play mp3s AHHHHHHHH

---

### Post by ceros on 2006-08-31
It's a xine bug. MP3's and Wave files won't play unless you mount the share. Take a look at the bugreport [here]("http://sourceforge.net/tracker/index.php?func=detail&aid=1494178&group_id=9655&atid=109655").

---

