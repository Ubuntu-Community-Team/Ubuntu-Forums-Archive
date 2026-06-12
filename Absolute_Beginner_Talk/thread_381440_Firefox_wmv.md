---
title: "Firefox wmv?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-03-10
Ok I know there's a million posts about this already but I still can find the answer to my question. I can't get wmv's to play with my mplayer plugin. I have w32 codecs and mplayer on my desktop plays them just fine. The problem is firefox always asks me "what I want to do with them" and I want it just to play in the embeded mplayer. In my download actions menu for wmv is has "Open with Windows Media Player plugin". How do I change this thanks.

---

### Post by 67GTA on 2007-03-11
That is what it should say. It will use the 32 codecs in mplayer. Have you installed the mplayer plugin for mozilla? What plugins are listed in user/lib/mozilla/plugins and user/lib/mozilla-firefox/plugins? You might need to reinstall mplayer plugin for mozilla and make sure the libtotem plugins are not in those folders. Also check about : plugins in firefox and see what is listed.

---

### Post by thelocust on 2007-03-11
Thats the whole thing is all the other codec work I have the mozilla-mpalyer plugin for firefox and they play just fine in firefox even wmv's play everyonce in a while. Heres my folder contents:

/usr/lib/mozilla/plugins$ ls
.                      mplayerplug-in-gmp.xpt  mplayerplug-in.so
..                     mplayerplug-in-qt.so    mplayerplug-in-wmp.so
libjavaplugin_oji.so   mplayerplug-in-qt.xpt   mplayerplug-in-wmp.xpt
libnullplugin.so       mplayerplug-in-rm.so    mplayerplug-in.xpt
mplayerplug-in-gmp.so  mplayerplug-in-rm.xpt

/usr/lib/mozilla-firefox/plugins$ ls
.  ..  libjavaplugin_oji.so

---

### Post by oilchangeguy on 2007-03-11
i used automatix to install all codecs, mplayer, etc. and i'm able to play video thru windows media player. try [www.getautomatix.com](www.getautomatix.com) i guess it would help if read your post more carefully. not sure how to make it play without asking what do you want to do.

---

### Post by Fíona on 2007-03-11
Have you installed the media connectivity add on for firefox? I found it helped.
Have you read the following?

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs).

---

