---
title: "ctrl+alt+backspace does nothing"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by SpikeyMike on 2006-11-13
Hi

I am trying to install the nvidia drivers using a guide I found on the forums and part of it involves using a command line by pressing ctrl+alt+f1 I have done this but now I can't get back to the desktop, the guide says ctrl+alt+backspace should do this but it doesn't work, I am using Edgy btw, please help

Spikey

---

### Post by joshsherman on 2006-11-14
Try alt+ctrl+F7 (or F8) that should take you back.

When installing the nvidia drivers, you should have went through the steps to kill GDM, you may want to start / restart GDM to get the whole situation working again.

sudo /etc/init.d/gdm start (or restart)

-j

---

