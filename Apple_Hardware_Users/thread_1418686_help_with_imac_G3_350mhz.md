---
title: "help with imac G3 350mhz"
date: 2010-02-28
forum: Apple Hardware Users
---

### Post by hal9k2010 on 2010-02-28
need help with this imac G3 350mhz 512 megs xubuntu 9.04 PowerPC version, everything works great exept the colors are funny looks like a very low color deph.
 i have some limited linux experience with other distros but very very new to ubuntu and limited comand (terminal ) experience. please if anybody can help ? thanks

---

### Post by tgalati4 on 2010-02-28
Read through:

less /var/log/Xorg.0.log

Make note of errors, what type of video hardware you have, default resolutions, etc.

Also, post the output of /etc/X11/xorg.conf

Make a backup copy:

sudo cp xorg.conf xorg_wonky.bak

Edit xorg.conf with appropriate settings.

Control-Alt-Backspace or Reboot.

If you can't get it to work, they do make a good fishtank.

---

### Post by linuxopjemac on 2010-03-01
you have to pick the right Xorg.conf file here:

[http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf](http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf)

---

