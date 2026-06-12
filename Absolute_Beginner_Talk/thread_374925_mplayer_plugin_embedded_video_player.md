---
title: "mplayer plugin embedded video player"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-03
Hello again,

whenever mplayer attempts to play content in firefox, it will buffer up to 99%, continue to download until complete, but not actually play anything.  It just shows the mplayer "splash" and some control buttons.  I don't think that codecs are the the issue as the file I am attempting to access is a .wav.  

If I access the Applications -> sound & video menu from the task bar, there is no mplayer listed.  When I used the add/remove function both mplayer and the plugin were showing as already installed. 

Sites like youtube work fine, but any site that used the quick-time plugin in XP seem to get this error.

I am using the 64 bit version of edgy and downgraded firefox to 32 bit this morning.  Any suggestions?

Thanks in advance!
Brian

---

### Post by rajeev1204 on 2007-03-03
hi

its true . Getting windows dlls to work in 64 bit is tricky. doesnt work for me 

U  have to install the 32 bit version of mplayer - try installing with automatix

Then it will play wmv 9 files.

---

### Post by marmaladejackson on 2007-03-04
OK... Automatix2 is only listing 64 bit packages... is there a way to get it to display the 32 bit ones as well?

---

### Post by Lanky Juggler on 2007-03-06
Probably won't help much, but i remember when i got a similar "99% loaded" thing, i would just have to hit the play button one or two times and the movie would start up just fine.  Give it a shot for the time being.

---

### Post by fubarbundy on 2008-01-29
I ran into this problem and came up with a solution in my case. I found at least two things that will cause mplayer-plugin to keep buffering at 99%.

1) Too small a cache size (can be set in the right-click->configure dialog)
2) Incompatible (?) config options in an mplayer config file (e.g. ~/.mplayer/config) - I  had msglevel=all=0 set in my mplayer config, and mplayer-plugin would refuse to play. To solve this, I put that config option under a [gmplayer] heading:

[gmplayer]
msglevel=all=0

My theory is that mplayer-plugin buffers to a certain point, then tries to play. If the mplayer engine fails for any reason (not enough data to decode, invalid config file) the plugin will try to buffer indefinitely (?)

Hope this helps someone!

Incidentally, that msglevel option suppresses all those f-ing non-fatal error dialogues, e.g. 'too many packets in buffer' :)

---

