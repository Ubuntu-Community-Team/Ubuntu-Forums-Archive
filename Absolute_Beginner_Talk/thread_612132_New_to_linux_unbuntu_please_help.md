---
title: "New to linux unbuntu please help"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by mx_racer84 on 2007-11-13
im using the latest version of unbuntu and im trying to install adobe flash player

i download the latest tarz.gz file and im trying to install it and i keep getting this error message im trying to figure out how to fix . Please help 
 

Here is the error message..

jamieson@jamieson-laptop:~$ '/home/jamieson/Desktop/Link to install_flash_player_9_linux.tar.gz' ./flashplayer-install
bash: /home/jamieson/Desktop/Link to install_flash_player_9_linux.tar.gz: Permission denied
jamieson@jamieson-laptop:~$

---

### Post by taurus on 2007-11-13
```
cd ~/Desktop
tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash
sudo ./flashplayer-install
```

---

### Post by anemptygun on 2007-11-13
An easier way to install flash player is to just download it in the add/remove applications. First when you open up add/remove apps, you need to enable all programs. So in the top right where it says ubuntu supported apps, change this to all available apps. Then go to other. Scroll down to Ubuntu restricted extras and install this package :) !

---

### Post by Paul820 on 2007-11-13
Flash is in the repositories for gutsy
> sudo apt-get install flashplugin-nonfree

---

### Post by mx_racer84 on 2007-11-13
still having a problem but thanks for trying here is the error message now

jamieson@jamieson-laptop:~$ cd ~/Desktop
jamieson@jamieson-laptop:~/Desktop$ tar xvzf install_flash_player_9_linux.tar.gz
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
jamieson@jamieson-laptop:~/Desktop$ cd install_flash
bash: cd: install_flash: No such file or directory
jamieson@jamieson-laptop:~/Desktop$ sudo ./flashplayer-install
sudo: ./flashplayer-install: command not found
jamieson@jamieson-laptop:~/Desktop$

---

### Post by taurus on 2007-11-13
```
cd install_flash_player_9_linux
sudo ./flashplayer-installer
```

---

### Post by mx_racer84 on 2007-11-13
whats this mean ?

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla):

---

### Post by taurus on 2007-11-13
It means where does the plugin for mozilla/firefox locate?  Just hit the Enter because there is where it is, /usr/lib/mozilla/plugins.

---

### Post by mx_racer84 on 2007-11-13
WARNING: /home/jamieson/Desktop/install_flash_player_9_linux/i.e., /usr/lib/mozilla is not a directory.

it doesnt seem to work it just keeps going back to the same message but with this ?

---

### Post by nickbooker on 2007-11-13
For firefox, it's /usr/lib/firefox

It's better to install it through Add/Remove Programs as described above though.

Select all applications from the drop down, and type flash in the search box.  Tick the box next to Macromedia Flash Plugin (as it's called in Feisty -- it might be Adobe Flash in Gutsy) and click Apply.  Just say yes if it asks you if you want to enable extra repositories or channels.

---

### Post by taurus on 2007-11-13
Why don't you enter /usr/lib/mozilla when it asks you where you want to install flash plugins.

Otherwise, just do this.
```
mkdir ~/.mozilla/plugins
cp flashplayer.xpt ~/.mozilla/plugins
cp libflashplayer.so ~/.mozilla/plugins
```

---

### Post by mx_racer84 on 2007-11-13
wow it worked thanks for all your help guys 

do u kno the code for installing limewire ?

---

### Post by mx_racer84 on 2007-11-13
thanks alot guys i got it working but i still cant figure out how to get bit torrent working it says its preloaded on the operating system but i cant seem to find it anywhere ?

---

### Post by anemptygun on 2007-11-13
I know, I could never find it either. but may i recommend Deluge torrent

[http://deluge-torrent.org](http://deluge-torrent.org)

or Ktorrent (under add/remove programs)

---

### Post by Sef on 2007-11-13
> thanks alot guys i got it working but i still cant figure out how to get bit torrent working it says its preloaded on the operating system but i cant seem to find it anywhere ?

The icon needs to be put on the menu list.  To do that follow these directions:

System > Preferences > Main Menu > Internet > click on BitTorrent > click on close.   It will show up in you menu under Internet.

---

### Post by anemptygun on 2007-11-13
> **Sef said:**
> The icon needs to be put on the menu list.
wow I never would have guessed that!

---

