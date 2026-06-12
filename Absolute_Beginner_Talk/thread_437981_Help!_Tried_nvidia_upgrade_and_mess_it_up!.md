---
title: "Help! Tried nvidia upgrade and mess it up!"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by rogerdw on 2007-05-09
Total Ubuntu newbie who should have left well enough alone! I decided to install the latest nvidia drivers into Ubuntu 7.04. Everything everything seemed to go correctly till I restarted the X windows and now its broken. Apparently I have messed up the config file somehow and I only have access through the terminal.

Any advice on how to reset my file to its original state would be greatly appreciated. Is there a backfile that I could restore the settings from? Where might I find it?

Roger

---

### Post by Nythain on 2007-05-09
at the command line you could try
sudo dpkg-reconfigure xserver-xorg
if that doesnt work then we are gonna need you to type
cat /etc/X11/xorg.conf
and put the contents here so we can get a glimpse of whats going on

---

