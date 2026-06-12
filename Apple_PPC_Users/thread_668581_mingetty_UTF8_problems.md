---
title: "mingetty UTF8 problems?"
date: 2008-01-15
forum: Apple PPC Users
---

### Post by curly_nostrill on 2008-01-15
hi all,

I'm running Xubuntu Feisty PPC on an iBook dual USB 600mhz with mpd playing music from a NFS share from a Freenas server over wireless trying to make a kiosk out of it.

I don't need X so I disabled GDM w/ the services control panel. I installed mingetty and have it --autologin=myuser on tty1 and tty2 and I added ncmpc to myuser's .bashrc.

The trouble is ncmpc looks and acts strangely on the mingetty tty's but works fine on the default getty tty's. I say UTF8? since I get some odd characters in the display. And as the play proceeds the screen gets garbled with lot's of this gobbledygoop. It straightens out somewhat when I scroll up and down the playlist but is pretty much back to the original not-quite-right display.

ncmpc uses ncurses. I'm using the ncmpc package from the repos. I tried to build ncmpc from SVN several times but no joy so far yet I still suspect mingetty anyway.

Anyone have any ideas? Maybe mingetty is not getting the right config for the locale or...?

Thanks

---

