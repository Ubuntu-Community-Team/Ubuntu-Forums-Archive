---
title: "search for XGL in Synaptic?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by FNDII on 2007-07-11
how do I search for XGL in Synaptic?

trying to follow this guide



To use the restricted driver (fglrx) to its full potential you need to use an XGL session (unlike Edgy there is no XGL session in Feisty)

So here how:

Code:

sudo apt-get xserver-xgl

(if this the apt-get code does not work than search for XGL in Synaptic)

Now:

Code:

sudo gedit /usr/local/bin/startxgl.sh

Fill the blank file with this:

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glxbuffer -accel xvbuffer &
sleep 4
export DISPLAY=:1
exec gnome-session

Then save.

Code:

sudo chmod a+x /usr/local/bin/startxgl.sh

Code:

sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop

Fill the file with this:

[Desktop Entry]
Encoding=UTF-8
Name=GNOME+XGL
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Then save.

Log out and hit sessions and select GNOME+XGL
Now log in as usual.

Make it default if you like. If done correctly you shoud see a grey screen that looks like steel wool with a black X for a cursor (or at with the steel wool in my case at least), the splash should look normal.

Enjoy!

If it looks choppy and garbled Completely uninstall XGL and reinstall it.
__________________

---

### Post by Happy_Man on 2007-07-11
Just open synaptic, hit the search button at the top, and enter "xgl". It should search the repos for you and put up whatever it finds. If you want a command line way to do it, ```
apt-cache search xgl
``` should do it.

---

### Post by Papi-KB7VGW on 2007-07-11
I found it with synaptic.  did a search for xgl and it was the last file in the list.  A lot of folks on the forum recommend using aptitude instead of apt-get for command line installs.  Good luck  :)


Edit:  Darn I'm too slow again!!!

---

### Post by FNDII on 2007-07-11
> **Happy_Man said:**
> Just open synaptic, hit the search button at the top, and enter "xgl". It should search the repos for you and put up whatever it finds. If you want a command line way to do it, ```
apt-cache search xgl
``` should do it.

Ok not sure what exactly that did for me but I put that line in the prompt

gnome-compiz-manager - Compiz Gnome Manager
libgnome-compiz-manager0 - Compiz Gnome Manager
libgnome-compiz-manager0-dev - Compiz Gnome Manager
python-wxglade - GUI designer written in Python with wxPython
spe - Stani's Python Editor
t1lib-bin - Type 1 font rasterizer library - user binaries
xserver-xgl - GL-based X server

What does this do in reference to the guide?

---

### Post by Papi-KB7VGW on 2007-07-11
Like I said above let synaptic install it for you.  search for xgl and right click on xserver-xgl  select mark for installation and let it do the work for you.

---

### Post by FNDII on 2007-07-11
I'm sorry I've only had it for 2 days ><

Whats "synaptic "?

---

### Post by FNDII on 2007-07-11
How do I do a search in synaptic?

---

### Post by Papi-KB7VGW on 2007-07-12
You will find very detailed documentation on synaptic at
[https://help.ubuntu.com/7.04/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.04/add-applications/C/advanced.html#synaptic)
That site is the official documentation for Ubuntu.  I suggest you spend some time there to make your Ubuntu experience a happy one

---

