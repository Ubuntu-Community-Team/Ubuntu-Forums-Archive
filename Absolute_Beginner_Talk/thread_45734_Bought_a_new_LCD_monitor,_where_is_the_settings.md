---
title: "Bought a new LCD monitor, where is the settings?"
date: 2005-07-01
forum: Absolute Beginner Talk
---

### Post by robertzhong on 2005-07-01
Hi, all
Getting luckier every day with Ubuntu !
A few days ago, I had problems with mouse scrolling, messed up with Xserver config, ended up resinstall the Ubuntu.

NOW the mouse wheel is working !! don't know why? but happy :-P  :-P .

Today I bought a new LCD monitor ( 17" philips 170s), trying to confirm that Ubuntu will auto detect the monitor, but I have no clue where to find the settings for monitor.

I have been to system menu and system tools but failed to find anything to do with monitors, can anyone help please?

Also I like the default font of Ubuntu, the font I am using to type this message, don't know it's name ? anyone has ideas?

Thank you !
robert zhong

---

### Post by intangible on 2005-07-01
CTRL-ALT-F1  log in with your username and password, then:

To reconfigure server for different screen:
**sudo dpkg-reconfigure xserver-xorg**

I believe the font is "Bitstream Sans".

---

### Post by rachii on 2005-07-01
hey, i believe the default font is "Sans"

for your monitor, i think you have to edit your xorg.conf to match the settings of the new monitor.  i dont know why it wouldnt auto set them...```
sudo gedit /etc/X11/xorg.conf
``` (or whatever your favorite editor is, gedit just works good for howtos)
and under the "monitor" section, the settings for your old one probably wouldnt work for your new one.

---

