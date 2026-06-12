---
title: "Did I install Flash wrong?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-16
(Running Xubuntu 6.10.) I'm new to Ubuntu. When I went to a website in Firefox that used Flash, I just followed the prompts to download the Flash player. But now every Flash site I go to slows down or hangs. I found [this site]("http://www.psychocats.net/ubuntu/flash") that says I should use aptitude to install Flash. I don't even know what aptitude is. Did I install Flash wrong?

---

### Post by taurus on 2007-03-16
Either follow that link that you provided or use this one.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by pdxuser on 2007-03-16
I followed your link and it said, "Install the package flashplugin-nonfree. You will need to have added the Multiverse component for this package to be present. See InstallingSoftware"  I followed the instructions at InstallingSoftware and added the Multiverse component.  But I don't see where I'm supposed to find the package flashplugin-nonfree for installation.

---

### Post by Sef on 2007-03-16
Since you have opened Multiverse, to get Flash easily follow these directions:

Applications > Add/Remove > in search, type in Flash > if it is checked, then it is installed > if it is not checked then click on it and click on Apply > follow the directions (click a couple of more times.)

---

### Post by pdxuser on 2007-03-17
Add/Remove Applications shows:

Macromedia Flash Player plugin installer 
Version: 7.0.68~ubuntu3 (flashplugin-nonfree)

But the page I found says to get rid of flashplugin-nonfree and to install Flash 9 located here:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

I had Add/Remove find the latest packages, so why wouldn't it have Flash 9?

---

### Post by aysiu on 2007-03-17
If you don't have the Edgy backports repositories enabled, the Flash version will be 7 instead of 9.

You have two major options (as detailed in the page you linked to):

1. [Enable extra repositories (including Edgy backports)](http://www.psychocats.net/ubuntu/sources) and then install Flash 9 by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

2. Forget about the repositories' version and install Flash 9 from the Adobe website by copying and pasting these commands into the terminal: ```
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
rm install_flash_player_9_linux.tar.gz
rm -r install_flash_player_9_linux
``` If you don't know what this whole business about repositories and *aptitude* is, read this page:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It's probably good for you to understand some basic principles behind centralized software management, but for this particular task, you don't have to understand anything except how to copy and paste commands.

---

### Post by NoMoreVictoriaSecret on 2007-03-19
This worked well with no issues.. just make sure you copy each line not the whole code.. any plugin for opera??

Jon


> **aysiu said:**
> If you don't have the Edgy backports repositories enabled, the Flash version will be 7 instead of 9.

You have two major options (as detailed in the page you linked to):

1. [Enable extra repositories (including Edgy backports)](http://www.psychocats.net/ubuntu/sources) and then install Flash 9 by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

2. Forget about the repositories' version and install Flash 9 from the Adobe website by copying and pasting these commands into the terminal: ```
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
rm install_flash_player_9_linux.tar.gz
rm -r install_flash_player_9_linux
``` If you don't know what this whole business about repositories and *aptitude* is, read this page:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It's probably good for you to understand some basic principles behind centralized software management, but for this particular task, you don't have to understand anything except how to copy and paste commands.

---

### Post by panayic on 2007-03-22
Thanks ppl.it worked well for me too.:guitar:

---

### Post by Bias on 2007-03-22
I just downloaded fom the flash website and followed the instructions given on that site, this worked just fine, I seem to remember at one point I had to enter the path to the location of firefox, I think the one in the example had the last folder in the path wrong but trying that generated and error so found the correct path and it worked just fine. I am also using dapper.

---

