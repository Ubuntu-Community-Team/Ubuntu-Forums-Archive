---
title: "Using MPlayer in Firefox rather than Totem"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by rskovacs on 2005-11-17
Hi there-

I was wondering how to enable the mplayerplug-in to take preference over the Totem Firefox plugin, or how to uninstall the Totem plugin altogether.  I'd rather use MPlayer, but apparently just installing the MPlayer plugin isn't enough...please help.

---

### Post by adwait on 2005-11-17
Try installing the mozplugger
```
sudo apt-get install mozplugger
```

---

### Post by cstudent on 2005-11-17
I think the plugins take precedence in the order they are listed if you look at about: plugins. I don't know if or how you can change the order, although I would certainly like to if it is possible. However, this is a trick that worked for me. I just went into /usr/lib/mozilla-firefox/plugins and renamed the file libtotem_mozilla.so to libtotem_mozilla.so_disable.

Bill

---

### Post by Corvillus on 2005-11-17
The other thing you could try doing is removing the Totem plugins from the Firefox directory. What I did was

```
cd /usr/lib/mozilla-firefox
sudo mkdir totemplugins
sudo mv libtotem_mozilla.* totemplugins
```

After doing that and restarting Firefox it used the MPlayer plugin instead.

---

### Post by rskovacs on 2005-11-18
Thanks everyone - what I actually ended up doing was taking Corvillus' advice.  Just one thing though - the plugins, on my system at least, were located in /usr/lib/mozilla-firefox/plugins , so, for anyone else who happens upon this thread...you might want to try

```

cd /usr/lib/mozilla-firefox/plugins
sudo mkdir totemplugins
sudo mv libtotem_mozilla.* totemplugins

```

But anyway, thanks everyone!  My one problem with Ubuntu so far has been the trouble it's been just to watch movies, but now I can! :D

---

### Post by zerhacke on 2005-11-18
Hold up a second... there's a totem plugin for Firefox?

---

### Post by statico on 2005-11-29
It appears that plugins listed in one's ~/.mozilla/plugins directory have precedence over system plugins. Thus, you can do the above without root or touching files managed by Ubuntu's package management system:

```
mkdir -p ~/.mozilla/plugins
cd ~/.mozilla/plugins
for f in /usr/lib/mozilla/plugins/mplayer*; do ln -s $f; done
```

---

