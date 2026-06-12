---
title: "[Need] Flash Player 7 for Xubuntu"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by iPhoenix on 2008-04-07
Recently installed Xubuntu on an old gateway. :)

I need a link or tut for installing flash player 7. I saw the the one posted here
[http://ubuntuforums.org/showthread.php?t=225592&highlight=xubuntu+flash](http://ubuntuforums.org/showthread.php?t=225592&highlight=xubuntu+flash)
But it did not seem to work for me.

If anyone could link me for Flash player 7 and terminal commands, it would greatly be appreciated.

iPhoenix

---

### Post by djbsteart1 on 2008-04-08
Why flash 7, isn't flash at 9 now or am I being silly? The first place I would look would be the adobe site if you want a legacy version. If its the current one, check that you have all of the software sources checked in software management and search for flash in the package manager. If this doesn't work, go to a website that needs flash and it should install the plugin automatically.

Donald.

---

### Post by ZeSteves on 2008-04-08
if you want flash 9 you can do 2 steps:

1. go to synaptic and search for[COLOR="DarkRed"] flashplugin-nonfree.[/COLOR] , then install it and reboot your browser.

the other way is go to this website: [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)
download the tar.gz and then :

[COLOR="DarkRed"][COLOR="DarkRed"]tar -zxvf install_flash_player_9_linux.tar.gz[/COLOR]
[COLOR="DarkRed"]
cd install_flash_player_9_linux/
[/COLOR]

[COLOR="DarkRed"]./flashplayer-installer[/COLOR][/COLOR]

i installed using the 1 method and it worked fine for me. try searching for version 7 in the adobe link.

good luck:)

---

### Post by wolfen69 on 2008-04-08
in terminal:
```
sudo apt-get install flashplugin-nonfree
```

---

