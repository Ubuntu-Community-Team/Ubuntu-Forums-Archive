---
title: "FireFox is trying to use Totem instead of MPlayer"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-11-18
I just installed Eft, and ran Automatix2 to get all of my codecs, etc..  For some reason, however, FireFox is trying to use Totem to play streaming radio (off of xmradio.com) instead of using MPlayer.  This is causing me to get an error.  How can I make that change?

Thanks.

---

### Post by aidanr on 2006-11-18
i had to remove the totem plugin from /usr/lib/mozilla/plugins and/or /usr/lib/firefox/plugins to get it to use mplayer instead of totem, i'm not sure if theres a way to tell it to use the mplayer plugin while the totem plugin is installed

---

### Post by aysiu on 2006-11-18
Deleting the Totem plugins can work.

You can also change the association in Edit > Preferences > Content > File Types > Manage

---

### Post by ajgreeny on 2006-11-18
I had to remove the totem plugin as well to get mplayer to play various files rather than totem, which often wouldn't play them anyway.  Setting file associations didn't seem to make any difference to my system, unless I've just not done it right.

---

