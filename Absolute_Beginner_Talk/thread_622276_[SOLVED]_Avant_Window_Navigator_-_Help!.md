---
title: "[SOLVED] Avant Window Navigator - Help!"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by ebennett on 2007-11-24
This is my first post, and I am an absolute beginner having little to no experience with linux.  So far doing fairly well, getting past issues using this forum..  

My problem is that I am trying to install the mac like doc (avant-window-navigator), and I get almost all the way through the instructions found at [http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html](http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html).  Then I get errors running the command ./autogen.sh.

------------------------------------------------------------------------
[FONT="Courier New"]earl@ZULU-3:~/installs/avant/avant-window-navigator$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build avant-panel-menu.  Download the appropriate package for
  from your distribution or get the source tarball at
    [ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz](ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz)

checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?
[/FONT]------------------------------------------------------------------------

Can anyone help me out, I am so close..

---

### Post by WiFi Ed on 2007-11-24
I had great success following the how-to posted here:

[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

---

### Post by stefanza on 2007-11-24
On Gutsy I installed AWN and AWN applets through System>Adminstration>Synaptic Package Manager.  Worked fine and updates as it registered via Synaptic.

---

### Post by Paul820 on 2007-11-24
You can get a deb file from here [http://www.getdeb.net/]("http://www.getdeb.net/")

---

### Post by ebennett on 2007-11-24
Tried that.  Afterwords when I try to launch the AWN it displays a grey box in the upper left for a fraction of a second, then goes away.

---

### Post by Pumalite on 2007-11-24
You have to have compiz-fusion working.

---

### Post by ebennett on 2007-11-24
I believe that I have all the correct compiz* packages installed, and I can run the compiz config manager..

---

### Post by scxtt on 2007-11-24
here's what i did, for feisty:
```

# sudo aptitude install bzr gnome-common gnome-common libglib2.0-data libglib2.0-dev automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf python-dev python-gtk2-dev python-cairo-dev

# bzr co http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator 

# AS ROOT: cat /usr/share/aclocal/libtool.m4 >> /usr/share/libtool/libltdl/aclocal.m4 
           touch /usr/share/pygtk/2.0/defs/gconf.defs 

# ./autogen.sh && make && sudo make install
# cd avant-window-navigator 


```this will build it from source, which i've had better luck w/ (feature wise) then pre-compiled packages ...

---

### Post by digitalcat on 2007-11-24
> **ebennett said:**
> I believe that I have all the correct compiz* packages installed, and I can run the compiz config manager..
You can run the compiz config without enabling Compiz, I think. I added a startup program for Compiz in System --> Preference -->sessions, and use "compiz --replace" as the command. That should start Compiz everytime you log in. 

Sorry if I was stating the obvious, just another newbie trying to be of some help, :)

---

### Post by ebennett on 2007-11-24
gave it a try..  same thing..  does this error mean anything to you?


Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200026 (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

The error above was generated when I started compiz via the terminal, then tried to bring up the AWN.

---

### Post by Paul820 on 2007-11-24
Do you not have a menu item for AWN? There is a menu item under Applications->Accessories->Avant Window Navigator. Do you have compiz fusion working?

---

### Post by Pumalite on 2007-11-24
Make sure you followed this:

First add my AWN repo: (this is a two-line command, paste the entire thing into ther terminal at once.)
Code:

echo 'deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator' | sudo tee -a /etc/apt/sources.list

Then add my apt key:
Code:

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc


Then install AWN:
Code:

sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

That's it!

---

### Post by ebennett on 2007-11-25
I wonder if it has something to do with the hardware.  IBM Thinkpad A31.  Before I took the plunge I was running xp with object dock, and I looked ok...

Currently.......
Compiz-fusion is installed
Avant Window Manager is installed
The AWM looks like it is starting for a fraction of a second, then aborts.


If I can't get the AWM going, is there another 'good' dock like option for gnome?

---

### Post by dinuop on 2007-11-27
hi all

me too having same prob with AWN

i cant see the doc

i installed through offline

ERROR:
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed

&



Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x600028 (awn_elemen)



can anybody help me out in this regard

i m using amd64bit 7.10

thanks in advance

---

