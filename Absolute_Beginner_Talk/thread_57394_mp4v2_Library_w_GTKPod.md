---
title: "mp4v2 Library w/ GTKPod?"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-08-16
```
Import of '/home/clayton/Music/Wehrwolfe/Godless We Stand/01 01. Unholy Crusade.m4a' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.
```

When I try to import some of my songs to my iPod Mini using GTKPod I get the error code above.  Is there any way to get the application to support these file types?

I need my tunes (This happens with alot of my favorite albums)!

---

### Post by KingBahamut on 2005-08-16
Hmmmm thats a good one. 

[http://www.mpeg4ip.net/](http://www.mpeg4ip.net/) mebbe...I dunno. Dont really do much with iPod.

---

### Post by the_purulent on 2005-08-16
They play fine through the XMMS and other audio players, but I cannot copy them to my ipod.

---

### Post by REBELinBLUE on 2005-08-16
[QUOTE=the_purulent]They play fine through the XMMS and other audio players, but I cannot copy them to my ipod.[/QUOTE]
 exactly the same thing happens to me

---

### Post by REBELinBLUE on 2005-08-17
Well I managed to get it working by building gtkpod with mp4 support manually, have to install a fair few dev packages. If I knew how to make a deb I'd package it up for you

---

### Post by REBELinBLUE on 2005-08-17
Another bump from me. Here it is

Since the forum doesn't allow deb packages to be attached you'll need to extract this file first

Remove gtkpod from synaptic first

```
tar zvxf gtkpod.tar.gz
sudo dpkg -i gtkpod*.deb
```

It doesn't create a menu shortcut, use Smeg to do that or just issue the command gtkpod.

Hope that helps you

---

### Post by the_purulent on 2005-08-17
Thank you!
I'll give it a try as soon as I get home from work tonight :)

---

### Post by the_purulent on 2005-08-18
Hmmm... Ok everything seems to have worked fine (followed your instructions above), however when I try to run gtkpod nothing happens.  The program is in /usr/bin and it shows up in my run programs list but when I run it ... nothing.

Do I need to re-install gtkpod-aac? (seems as though that would remove the one you created).

---

### Post by the_purulent on 2005-08-18
Buuuuuump!

---

### Post by REBELinBLUE on 2005-08-19
[QUOTE=the_purulent]Buuuuuump![/QUOTE]
 hmm, I'm really not sure sorry. I don't have a fresh ubuntu install I can try it on

---

