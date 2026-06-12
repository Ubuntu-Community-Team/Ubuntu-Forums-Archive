---
title: "Canot install Xserver"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by wadeall on 2006-11-02
I'm running  (or at least I was) Edgy.  I had the thing running pretty well then tried to get clever and try and install the  up to date nvidia drivers as per Tseliot's how to.

Unfortunately this stopped the GUI on my system and I have been unable to reinstall xserver.

When I try to I get an error:

cannot stat /etc/X11/X ubuntu

Any idea what I can do or  will I  have to  do a completee reinstall?

---

### Post by dillbertdabomb on 2006-11-02
Nvidea cards are not officially supported, I think nvidea has offical drivers for linux, but ubuntu won't include them becuase there not open sorce.

too bad ubuntu.

---

### Post by bulldog on 2006-11-02
Try in command line mode,```
sudo dpkg-reconfigure -phigh  xserver-xorg
```
to reconfigure your xserver.

You can try this if reconfigure doesn't do the trick.```
sudo nano /etc/X11/xorg.conf
``` and replace nvidia for nv in sectio device.
ctrl-x to close and enter to save the file.

---

### Post by wadeall on 2006-11-02
Im Afraid  when I try the sudo dpkg-reeconfigure -phigh xserver't work - it just returns:

/usr/sbin/dpkg-reconfigure: xserver is not installed

The drivers are already nvidia rather than nv

So Im afraid  Im still stuck, though thanks for the suggestions

---

