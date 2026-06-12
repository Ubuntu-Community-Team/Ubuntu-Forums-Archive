---
title: "Installing Awn"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by windows hater on 2008-03-16
 I love compiz and all the neat animations it can do but i heard a lot about this docking thing awn and its seems cool i have found how to install it but I'm lost at how to do it can some one please help 


[http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html]("http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html")

---

### Post by bumanie on 2008-03-16
As you are using feisty, this guide may be better. [http://awn.wetpaint.com/page/UbuntuFeistyHowTo?t=anon](http://awn.wetpaint.com/page/UbuntuFeistyHowTo?t=anon)

---

### Post by windows hater on 2008-03-16
im sry im using gutsy right now  but im lost on what this link is saying in the beginning and i would just like it if some explained it or just showed step by step to on how install awn

---

### Post by bumanie on 2008-03-16
OK, you haven't your details, no sweat.
You firstly need to open terminal and type code
> sudo gedit /etc/apt/sources.list
When it opens copy and paste these two lines 
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
to the bottom of the list and then save the changes.
Then copy and paste the bolded lines into terminal one at a time, hitting enter between each line.
Then in terminal type this
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Followed by this allat once
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev gnome-icon-theme python-glade2 librsvg2-common, python-gnome2-extras
Then this one line at a time hitting enter in between
bzr checkout [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
cd avant-window-navigator
./autogen.sh
make
sudo make install

---

### Post by windows hater on 2008-03-16
umm how might i noe if it works

---

### Post by WiFi Ed on 2008-03-16
This how-to worked well for me...

[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

After installation, go to Applications/Accessories/Avant Windows Manager

---

### Post by windows hater on 2008-03-16
thank you i got it installed but now i got a new problem its located at the bottom of the screen is there anyway to like move it

---

