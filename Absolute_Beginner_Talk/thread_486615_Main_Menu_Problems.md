---
title: "Main Menu Problems"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ahoman66 on 2007-06-28
I have installed Ubuntu 7.04 on my sons PC and I can not access the main menu to wine to the Applications list. If I try from the System-Preferences I get the same problem. It shows it starting them it goes away.  He is a real big cs 1.6 and cs:source player and now has a killer Ubuntu box that kills winblows...

Thanks for the help
Allen

---

### Post by rajeev1204 on 2007-06-28
This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/bugs/97460](https://bugs.launchpad.net/bugs/97460)
----------------------------


yes its a confirmed bug

Type these commands in a terminal .

sudo chown -R <user> ~/.local/share/applications
sudo chown -R <user> ~/.config/menus


Some home files (mentioned above) end up being owned by root so alacarte cant save entries


The above commands will change back ownership to you
__________________

---

### Post by ahoman66 on 2007-06-28
Thank you very much for the help.

Allen

---

