---
title: "un-installing Wine"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-10
[COLOR="DarkRed"]Hello. I would like to un-install wine, does anyone know the path or how to do that please>

Thank you Sherri[/COLOR]

---

### Post by inchaos on 2007-04-10
To uninstall Wine, just go to add/remove applications, search for 'Wine', and deselect the box next to the package.
Click 'apply' followed by 'OK' and it will uninstall.

To simply uninstall a program in Wine, in terminal just type 'uninstaller' and a Wine Application Uninstaller will pop up that will allow you to uninstall any Windows programs you no longer want.

:)

---

### Post by delilahjed44 on 2007-04-10
[COLOR="DarkRed"]Hello, thanks for the reply, wine is not in the add/remove programs I tried this.  I cant open wine to do as you say, how do I open wine? it opens some of my programs because I can right clik and use it, but I want to un-install it, how can that be done if I am cant find the path to do as I wish? where is the path to open it as you say above, and when found how can I un-install it,

Sherri[/COLOR]

---

### Post by Efros on 2007-04-10
open a terminal and try

sudo apt-get remove wine

---

### Post by inchaos on 2007-04-10
Wine doesn't have an interface so you can't just open it, you use it in order to open other programs, like you said.  This confused me at first too.

It should be in your add/remove apps, if not you can try to remove it with Synaptic.  If that doesn't work, try this in a terminal:

$ sudo apt-get remove --purge wine

(I haven't tried this myself, I got it from [http://ubuntuforums.org/showthread.php?t=403469&highlight=uninstall+wine]("http://ubuntuforums.org/showthread.php?t=403469&highlight=uninstall+wine[/URL"))

Hope it works!

---

