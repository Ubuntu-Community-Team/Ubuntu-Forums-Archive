---
title: "[SOLVED] Multimedia Keys in KDE/Arch"
date: 2008-11-20
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-11-20
Being new to KDE, I'm wondering what would be the best way to setup the multimedia keys of my laptop. I looked in system settings but can't seem to find anything relevant. 

Currently the front-panel multimedia keys don't work in Arch/KDE. Any help is much appreciated.

---

### Post by fwojciec on 2008-11-20
You can try if the keys in questions are actually recognized by the system by running xbindkeys -mk, pressing the keys and seeing if they produce any codes.  If they do, then you can just use xbindkeys to bind them to specific commands.  If they don't then it's possible that you will not get them to work, at least not easily.

---

### Post by kpkeerthi on 2008-11-20
Sorry for not being very clear. The keys did work when I used GNOME. So Arch did recognize the keys. But, how do I set it up from within KDE without having to install additional programs like xbindkeys, keytouch, etc. ?

If GNOME could do it, I assume KDE should also be. Or is xbindkeys/keytouch is the only answer?

---

### Post by kpkeerthi on 2008-11-22
I tried KDE4 for a week. It is not for me. KDE4, at the moment, is only half-done. I'm much happier with XFCE. Stable & just works (of course with a bit of post installation tweak typical of Arch).

---

