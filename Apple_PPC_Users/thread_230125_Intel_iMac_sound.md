---
title: "Intel iMac sound"
date: 2006-08-05
forum: Apple PPC Users
---

### Post by irTESEV on 2006-08-05
Has anyone gotten the sound to work on an Intel iMac?  I am currently using external speakers but would like to put them back on my other mac and use the internal speakers on the iMac.

---

### Post by jakemikey on 2006-08-14
Yeah - I'd really like to have this one solved - I'm having the same problem.

---

### Post by jazzman on 2006-08-14
The sound outputs on my G3 are opposite. If you were to plug in your speakers in the back of the mac your built in speakers work. If you plug speakers into the front jacks they work just fine.

Try plugging in an old pair of headphones in the rear sound jack and you might find that the built-ins work.

--Jazzman

---

### Post by hyperchickens on 2006-08-16
I dont have an intel imac (i have an old g3 one), but my built in speakers seemed broken untill i realized they were muted from the start and un-muted them. It may be a different problem but its probably worth checking out.

---

### Post by jakemikey on 2006-08-16
FIXED!

Found a link on setting up a Mac mini for MythTV:

[http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu#Sound](http://www.mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu#Sound)

All I had to do was:

alsamixer

and then use the r/l arrows and "m" to unmute all the channels, etc. but especially the IEC958. I then logged out/back in and everything worked!

Hope this helps.

---

