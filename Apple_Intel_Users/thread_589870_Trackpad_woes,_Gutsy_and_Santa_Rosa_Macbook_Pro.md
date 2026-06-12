---
title: "Trackpad woes, Gutsy and Santa Rosa Macbook Pro"
date: 2007-10-24
forum: Apple Intel Users
---

### Post by neatokino on 2007-10-24
I made a fresh install of Gutsy on my Macbook Pro (Santa Rosa), dual booting with OSX, and, as with Feisty, things work generally OK, but I am having terrible problems with the trackpad and keyboard.   

I edited the X.org configuration file per the wiki, but the X.org changes don't take effect at all.  I believe that something else (graphic interface trackpad control???) is taking precedent over the X.org trackpad instructions, but I can't for the life of me figure it out.

Any suggestions?  Has anyone else had these problems?

As it stands, I can't right click at all,  and the trackpad is so sensitive, I can't type on the keyboard without mouseclicks flying all over the place at random.

---

### Post by cleentrax on 2007-11-09
I'm having the same problem with a C2D Santa Rosa Mac Book. If I set the Synaptics as the Core Pointer, it breaks xorg.conf, saying that there is no Synaptics. Perhaps the synaptics driver no longer works on the latest/"greatest" apple trackpads.

---

### Post by matei125 on 2007-11-10
Can you post your xorg.conf? I've edited mine on my Santa Rosa machine with the instructions at [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa) and it seems to be working. To disable it while typing, make sure the SHMConfig option is set to "on" and add syndaemon -d -t to your session startup items as described on [http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/](http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/) .

---

### Post by hardawayd on 2008-01-10
How do you disable it in Hardy---I think Hardy uses a different version of xorg-server.

---

