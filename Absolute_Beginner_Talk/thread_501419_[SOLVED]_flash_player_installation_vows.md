---
title: "[SOLVED] flash player installation vows ?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Jasdeep on 2007-07-15
I wanted to run flash version of google talk in my browser , as it requires flassh version 9 .
I tried to install flash player 9 by many means thro tar ball, through rpm to deb conversion .
 but kubuntu does not let  me to do so.. It worked no probs with my Open Suse machine ..

My firefox  about:plugins show 4 flash player pulgins :

1. Shockwave Flash
    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

2  GPLFLash homepage : gplflash.sf.net
 File name: libflashplayer.so

3 Shockwave Flash 9.0 r31

4Shockwave Flash
    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

My locate firefox/plugins dump :

/usr/lib/firefox/plugins/mplayerplug-in-rm.xpt
/usr/lib/firefox/plugins/mozplugger.so
/usr/lib/firefox/plugins/libunixprintplugin.so
/usr/lib/firefox/plugins/mplayerplug-in-wmp.xpt
/usr/lib/firefox/plugins/mplayerplug-in-qt.xpt
/usr/lib/firefox/plugins/libflash-mozplugin.so
/usr/lib/firefox/plugins/mplayerplug-in.xpt
/usr/lib/firefox/plugins/mplayerplug-in-qt.so
/usr/lib/firefox/plugins/mplayerplug-in-wmp.so
/usr/lib/firefox/plugins/mplayerplug-in.so
/usr/lib/firefox/plugins/mplayerplug-in-rm.so_backup

but the google talk still yells :

Oops!

The Google Talk Gadget requires Adobe Flash Player version 9 or higher.
You can install the player here.

To complete the installation, quit all running instances of your browser.

Help me fix this ...

---

### Post by Jasdeep on 2007-07-15
thanx folks ..
i did it myself removed version 4 flash from plugins
[PHP]rm /usr/lib/firefox/plugins/libflash-mozplugin.so[/PHP]
and i got it running ...

---

