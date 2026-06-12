---
title: "Setting Screen Resolution"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by Mark Roberts on 2005-12-27
does any one know how to set screen resolution with ubuntu?

Here is my problem....When I first installed ubuntu, it auto set my screen to 1280 x 1024. The other day, I had a power fluctuation and failure. With the power came back up, my screen resolution was set to 640 x 480. Now I cannot change it. This setting makes my screen very large and I have to stand across the room to see it and then only about 1/4 of the screen shows.

When I go to settings/preferences/screen resolution...I have no options...only 640 x 480, No dropdowns and I cannot change it. I hate to wipe the disk and re-install the system (that I why I switched from windows, I got tired of doing that, now it looks like I might have to do that with ubuntu just to get control of my screen again).

Anyone have any ideas other that re-installing?

---

### Post by amohanty on 2005-12-27
try:

> sudo dpkg-reconfigure xserver-xorg

HTH
AM

---

### Post by daschl on 2005-12-27
[QUOTE=Mark Roberts]does any one know how to set screen resolution with ubuntu?

Here is my problem....When I first installed ubuntu, it auto set my screen to 1280 x 1024. The other day, I had a power fluctuation and failure. With the power came back up, my screen resolution was set to 640 x 480. Now I cannot change it. This setting makes my screen very large and I have to stand across the room to see it and then only about 1/4 of the screen shows.

When I go to settings/preferences/screen resolution...I have no options...only 640 x 480, No dropdowns and I cannot change it. I hate to wipe the disk and re-install the system (that I why I switched from windows, I got tired of doing that, now it looks like I might have to do that with ubuntu just to get control of my screen again).

Anyone have any ideas other that re-installing?[/QUOTE]

you can edit your xorg.conf :) (there are loads of tutorials in the internet, just look for it)

/etc/X11/xorg.conf
(maybe its a good idea to backup the file first)

---

