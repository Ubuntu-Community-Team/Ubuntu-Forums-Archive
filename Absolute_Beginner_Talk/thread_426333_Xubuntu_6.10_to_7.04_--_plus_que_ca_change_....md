---
title: "Xubuntu 6.10 to 7.04 -- plus que ca change ..."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-04-28
If you have updated you Xubuntu, did you notice any difference in functionality?  Because I haven't.
Am I dull?:-|

---

### Post by Blofeld on 2007-04-28
Hey, I found something!  Firefox plays Flash movies now with sound!
;-)

---

### Post by Blofeld on 2007-04-28
Still doesn't play my Onion Radio News, though ... dang!

---

### Post by Blofeld on 2007-05-07
OK, now I found something that really made the stony transition to 7.04 worth while:  my mic is now working and I can VoIP!
:-({|= 
Yesss ...

---

### Post by Blofeld on 2007-05-07
OK, the mic has just STOPPED working ...:confused:

---

### Post by Blofeld on 2007-05-08
I managed to get the mic to work again by appending the file ...
/etc/modprobe.d/alsa-base
... with the line ...
options snd-hda-intel model=ref
[-o<
Also I got Firefox to play Quicktime audio streams (such as Onion Radio News, [http://www.onion.com](http://www.onion.com)) by installing the MPlayer plugin for Firefox 2 via Automatix 2.

---

