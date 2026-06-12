---
title: "Install flash plugin for firefox(yes I've read the tutorials)"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by FrozenDice on 2006-06-18
I've read numerous tutorials on how to install flash for firefox, I even tried using flash's standalone installer but I couldn't get it to find the directory where firefox was located in.  Other people suggest using wine to emulate the windows firefox and plugin, which is such a waste.  Anyway, how do I use flash in ubuntu, I've also read that even when I get it working there will be no sound.  Sigh*  This is to be expected though, linux is always a work in progress.  I guess it's just sort of a shock since I've been using OS X for a while and it felt like everything was always running smooth with it.  I'm using ubuntu while my iBook is in the shop, and because I can't stand windows.  :) Any help appreciated.

---

### Post by mlind on 2006-06-18
```

 apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 7.0.63.3ubuntu3
  Candidate: 7.0.63.3ubuntu3
  Version table:
 *** 7.0.63.3ubuntu3 0
        500 http://fi.archive.ubuntu.com dapper/multiverse Packages
        100 /var/lib/dpkg/status

```

Tried installing flashplugin-nonfree from multiverse repository? It should work.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/Repositories/Ubuntu](https://wiki.ubuntu.com/Repositories/Ubuntu)

---

### Post by nalmeth on 2006-06-18
Sound does work in flash, but it's easily disabled. I don't exactly understand how/why it occurs, but it does. 

I never had any luck with the flashplayer-nonfree, I use the old flashplayer-mozilla from breezy.

You can find it on packages.ubuntu.com/

---

### Post by aysiu on 2006-06-18
Sound works in my Flash.

Instead of complaining that it doesn't work, why don't you explain what went wrong? What errors did you receive?

If you're installing it straight from the Macromedia site, try installing it to /usr/lib/firefox/plugins

---

### Post by forrestcupp on 2006-06-21
I just installed it to /usr/lib/firefox and it worked

---

### Post by Drakkor on 2006-06-21
automatix or easyubuntu

---

### Post by amunimanghi on 2006-06-21
I have it install but when I go to view a page that has flash, it says you need at least flash version 8. I downloaded the **install_flash_player_7_linux.tar.gz**. I looked in synaptic and its the exact same thing.

---

### Post by aysiu on 2006-06-21
There's no Flash 8 for Linux.

There will be a Flash 9, though.

---

### Post by amunimanghi on 2006-06-21
Yeah, I found out after I posted. :p

---

