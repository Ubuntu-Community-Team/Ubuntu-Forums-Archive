---
title: "xmatrix as desktop background"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by nwgray on 2006-10-24
Not sure if this needs to be in this forum so please bump to the correct one as needed.

I want to use xmatrix as my animated background. I use this command to test:

 sudo /usr/lib/xscreensaver/xmatrix -delay 20000 -small -density 40 -trace

this works flawlessly, but in it's own window.

If I add -root after xmatrix, nothing happens. The command doesn't error out or anything but nothing changes on the desktop. 

How can I get it to run as the background?

Thx everyone. This forum is the reason I use ubuntu!

P.S. 
   Tried using -root switch in Blackbox and it works fine. Must have something to do with nautilus.

---

### Post by CatKiller on 2006-11-30
I know this was a while ago, but that's cool.

You need to open **gconf-editor** and untick /desktop/gnome/background/draw_background

EDIT: And possibly /apps/nautilus/preferences/show_desktop too.

---

### Post by diablo69er on 2007-05-21
I am using feisty--but these cmds should be the same.

Try this and tell me if it works for you

sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.bak

sudo apt-get install linux-restricted-modules-'uname -r'

Now if you have a ATI card type in the following

sudo apt-get install xorg-driver-fglrx fglrx-control

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

sudo dpkg-reconfigure xserver-xorg

*will auto detect video card..be sure to select fglrx and not ati*  *keep defaults*

restart your x server by logging out and then logging back in

Let me know how this turns out for you :)

---

