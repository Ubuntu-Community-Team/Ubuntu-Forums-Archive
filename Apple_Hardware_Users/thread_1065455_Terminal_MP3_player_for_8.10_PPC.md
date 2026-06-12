---
title: "Terminal MP3 player for 8.10 PPC"
date: 2009-02-09
forum: Apple Hardware Users
---

### Post by abeisgreat on 2009-02-09
So I've got ubuntu 8.10 server installed on my old IMAC, mainly used for backup purposes, but I would like to be able to play music from the built in speakers. I installed... I think it was alsa, once before that allowed me to have sound, but I couldnt find a working terminal MP3 player, any help with finding a player/suitable codecs for mp3s?

---

### Post by logos34 on 2009-02-09
try mpg123 or, better yet, [moc]("http://moc.daper.net/image/tid/18") (ncurses display)

+ codecs

sudo apt-get install lame ubuntu-restricted-extras

---

### Post by marshag63 on 2009-02-10
+1 for MOC (start it by typing "mocp", use arrow keys to navigate through directories to your music, use < and > to turn volume up/down)

You can check your main volume settings with alsamixer (type alsamixer at terminal prompt and use arrow keys to move from setting to setting and adjust settings, "M" mutes/unmutes settings, press Esc key to exit).

MOC rocks!!!

MarshaG.

---

