---
title: "updating to flash 9"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-03-29
I've downloaded the install file and began to run it. The installation stops and ask me for the installation directory of mozilla and gives the example /usr/lib/mozilla. I've tried this and it doesn't work. I've navigated to this folder through the file browser and all it contains are one or two files and a folder called plugins. I tried saying tht /usr/lib/mozilla/plugins was the install path but it's still not accepting it. Where should I install it to?

---

### Post by bkeithly on 2007-03-29
What error message are you getting?

try this:

updatedb

then 

locate mozilla/plugins | more



If you really get a bad head ache with the flash update, try swift fox.  Works great for me!

---

### Post by woodsonoversoul on 2007-03-29
Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla):** /usr/lib/mozilla**
dir= /usr/lib/mozilla

WARNING: Please enter a valid installation path. /usr/lib/mozilla


That's what terminal says. I entered the bold

---

### Post by aysiu on 2007-03-29
This should help you:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by woodsonoversoul on 2007-03-29
I was following the steps on the phycocats page and when I entered

sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

It says those directories don't exist

---

### Post by aysiu on 2007-03-29
That's weird.

Can you post the output of these commands (in this order)? ```
cd /usr/lib
ls
cd firefox
ls
cd plugins
ls
```

---

### Post by woodsonoversoul on 2007-03-29
It says I don't have a firfox directory in /usr/lib
I have a mozilla directory, but no firefox

---

### Post by woodsonoversoul on 2007-03-29
Is there a search function where I could find my firefox directory. I mean I am using firefox...

---

### Post by Maestro23 on 2007-03-29
> **woodsonoversoul said:**
> Is there a search function where I could find my firefox directory. I mean I am using firefox...

Open terminal:

> whereis firefox

---

### Post by aysiu on 2007-03-29
> **woodsonoversoul said:**
> It says I don't have a firfox directory in /usr/lib
I have a mozilla directory, but no firefox
What version of Ubuntu are you using? 5.10?

---

### Post by devnulljp on 2007-03-29
Did you install it manually? (i.e. firefox2)
If you used apt-get / aptitude etc. you should have those folders.
I installed firefox 1.5.x using aptitude, then installed firefox2 manually in /opt/ thenused these instructions to make firefox2 the default: 
[http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html](http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html)

---

### Post by woodsonoversoul on 2007-03-29
ver 5.04

---

### Post by wpshooter on 2007-03-29
> **woodsonoversoul said:**
> I've downloaded the install file and began to run it. The installation stops and ask me for the installation directory of mozilla and gives the example /usr/lib/mozilla. I've tried this and it doesn't work. I've navigated to this folder through the file browser and all it contains are one or two files and a folder called plugins. I tried saying tht /usr/lib/mozilla/plugins was the install path but it's still not accepting it. Where should I install it to?

To the best of my recall, you need to install this program using the SUDO command.  I believe that is needed in order to give you access rights to the default directories that the install goes to.

Also, I think it is important that you are getting the program from the correct source.  Again, as I recall, if you do not get it from the proper site, it will not necessarily install correctly.

Good luck.

---

### Post by woodsonoversoul on 2007-03-29
I know I should probably get a newer version, but I've updated it, so I figured I would be caught up enough for most things. Could I just re-install firefox?

---

### Post by aysiu on 2007-03-29
> **woodsonoversoul said:**
> ver 5.04
In that case, follow the Psychocats tutorial but just sub in /usr/lib/mozilla/plugins for /usr/lib/firefox/plugins ```
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins/
```

---

