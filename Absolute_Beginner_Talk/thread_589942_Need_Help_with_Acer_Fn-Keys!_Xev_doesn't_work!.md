---
title: "Need Help with Acer Fn-Keys! Xev doesn't work!"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by MechChap on 2007-10-24
ARRRGH!!!! I've tried to set up my Fn-keys for days now. I've googled hard and searched hard and tried hard but none of the tutorials seem to work!! Most of them tell me to use xev which I did but only managed to get the scancode and keycodes for:

 Fn-Play/Pause
 Fn-Stop
 Fn-PreviousSong
 Fn-NextSong

AND NOTHING ELSE!!! 

Tried Key touch editor, tried going into ctrl-alt-F1 and used the showkey -m command, doesn't detect the Volume keys either. 

What I need to fix now are the volume keys, mute key, enable/ disable touchpad, wireless and bluetooth keys.

Can someone please point me in the right direction?
I am using Acer Aspire 5590 series
Model: Acer Aspire 5594WXMi

---

### Post by MechChap on 2007-10-25
Most of the tutorial links for this topic are broken. Can someone please point me in the right direction??

---

### Post by MechChap on 2007-10-25
anybody??

---

### Post by mali2297 on 2007-10-25
If xev gives you the keycodes, then you can use **xmodmap** to associate keysymbols. Here is a howto:
[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

---

