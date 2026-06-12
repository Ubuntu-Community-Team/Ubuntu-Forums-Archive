---
title: "trouble with flash plugin!"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by tiendn on 2006-10-21
HI!
  I have installed flashplayer, but when I come some website, I have seen some plugin not install,and I have reinstall flash but It has not changed?

---

### Post by jordanmthomas on 2006-10-21
In firefox, go to about:plugins and make sure flash is listed.

that smiley face is a colon and then a p

---

### Post by jqk on 2006-10-21
sudo apt-get install flashplugin-nonfree

flashplugin-nonfree is an Adobe Flash Player plugin installer, and that's what you need.

---

### Post by tuxrtfm on 2006-10-21
Some websites, MSNBC, for example require a newer version of flash.
If ```
about:plugins
``` says that your version of flash is not "Shockwave Flash 9.0 d55" I would try to update it.

I will look for a howto guide for you and post it.

---

### Post by tuxrtfm on 2006-10-21
Found It!
Open Termail
     [LIST=1]
[*]Applrcations
[*]Accessories
[*]Terminal
[/LIST]

Then type the following:
```

wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/firefox/plugins/
```

Restart Firefox

---

### Post by tiendn on 2006-10-21
I think too, but how to install it, I installed flashplugin-nonfree,

---

### Post by PriceChild on 2006-10-21
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)

is a howto on the forums

---

