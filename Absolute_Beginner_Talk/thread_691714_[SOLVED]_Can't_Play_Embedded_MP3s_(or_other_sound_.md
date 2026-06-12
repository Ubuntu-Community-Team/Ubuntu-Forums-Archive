---
title: "[SOLVED] Can't Play Embedded MP3s (or other sound files)"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by chrissy833 on 2008-02-08
I recently installed mplayer on my computer (I use firefox 2.0) and found that I could not play embedded mp3 files in firefox (instead I had to download them).  After tweaking with the settings, I got annoyed and uninstalled it.  When installing mplayer, I also installed a few other plugins (I can't remember exactly what; I know I'm stupid).  Now I have totem back as my default plugin, but I still can not play embedded mp3s.  I uninstalled and reinstalled Totem, and that did nothing.  Right now I get a black box that says "no video" instead of an mp3 player.  About: plugins says that I have the following plugins, all of which are enabled: libflashplayer.so 
libvlcplugin.so 
libtotem-basic-plugin.so
libtotem-gmp-plugin.so
libtotem-mully-plugin.so
libtotem-narrowspace-plugin.so

This includes the Totem plugin, which says that it plays mp3s.  I also have the VLC multimedia plugin, which I guess may not be compatible with Totem (I really have no idea).

---

### Post by ubuntu-freak on 2008-02-08
Try my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Should be all you need.
 
Nathan

---

### Post by chrissy833 on 2008-02-08
That worked wonderfully, thanks a ton.

---

### Post by ubuntu-freak on 2008-02-09
> **chrissy833 said:**
> That worked wonderfully, thanks a ton.

 
No problem. Glad to help.
 
Nathan

---

### Post by nikoPSK on 2008-02-09
> **reassuringlyoffensive said:**
> No problem. Glad to help.
 
Nathan

They should basically play after the gstreamer codecs. :)

---

