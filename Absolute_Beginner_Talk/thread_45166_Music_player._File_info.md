---
title: "Music player. File info ?"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by weasel fierce on 2005-06-29
Using the music player, but wondering.. is there any way to change the Artist and Album information for the songs I have ?

A lot of them are loaded as "unknown" in the list. If you right click, it'll give you boxes to change it.. except you cant.


Cheers!

---

### Post by bored2k on 2005-06-29
[QUOTE=weasel fierce]Using the music player, but wondering.. is there any way to change the Artist and Album information for the songs I have ?

A lot of them are loaded as "unknown" in the list. If you right click, it'll give you boxes to change it.. except you cant.


Cheers![/QUOTE]
 sudo apt-get install easytag

It's pretty straight forward.
[http://easytag.sourceforge.net/screenshots-gtk2.htm](http://easytag.sourceforge.net/screenshots-gtk2.htm)

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=bored2k]sudo apt-get install easytag

It's pretty straight forward.
[http://easytag.sourceforge.net/screenshots-gtk2.htm](http://easytag.sourceforge.net/screenshots-gtk2.htm)[/QUOTE]


I second that. Easytag is the best.

---

### Post by weasel fierce on 2005-06-29
Thanks a bunch :) I downloaded it and tried it out, but I am getting Permission denied, when I try to add tags and save it. What did I miss ? :-?

---

### Post by bored2k on 2005-06-29
[QUOTE=weasel fierce]Thanks a bunch :) I downloaded it and tried it out, but I am getting Permission denied, when I try to add tags and save it. What did I miss ? :-?[/QUOTE]
 Your MP3 files have read only permission. Right click - properties - permissions on them and check the boxes.

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=weasel fierce]Thanks a bunch :) I downloaded it and tried it out, but I am getting Permission denied, when I try to add tags and save it. What did I miss ? :-?[/QUOTE]


Well...are you doing it to a ntfs drive? Linux can't write to an NFTS drive. Are you files under root permission? (smart idea...I do that too), then do this command:

> gksudo easytag

---

