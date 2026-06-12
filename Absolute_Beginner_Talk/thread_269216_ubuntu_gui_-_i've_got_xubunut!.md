---
title: "ubuntu gui - i've got xubunut!"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by tospig on 2006-10-01
Hi,

I was following this guide: 

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+card](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+card)

as I was having problems with my sound, and I got to the part entitled: 

"Getting the ALSA drivers from a *fresh* kernel"

I was following the instructions, did the removal and re-install:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

but me being me i installed the wrong desktop, namely the xubuntu one:
sudo apt-get install gdm xubuntu-desktop

so therefore, I now have the xubuntu desktop running, and not the ubuntu one.

How do I go back to ubuntu? I've tried the steps again, tried removing gdm xubunut-deskotp, and installing gdm ubuntu-desktop, but it keeps taking me back to xubuntu!

when the system is rebooting I get the ubuntu load screen, but after that it goes to xubuntu.

any thoughts and comments greatly received :)

---

### Post by bodhi.zazen on 2006-10-01
You should be able to choose your window manager from one of the menu's at the log in screen.

---

### Post by tospig on 2006-10-01
ahhhhhh found it!!

thanks a lot :)

---

