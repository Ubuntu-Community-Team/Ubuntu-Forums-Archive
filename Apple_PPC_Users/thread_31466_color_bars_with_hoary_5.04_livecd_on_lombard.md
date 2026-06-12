---
title: "color bars with hoary 5.04 livecd on lombard"
date: 2005-05-03
forum: Apple PPC Users
---

### Post by secundar on 2005-05-03
Boots fine and runs thru config using video=ofonly but when i get to the gnome desktop i get a black screen full of color bars. Rather pretty but useless.

PowerBook G3 a.k.a. "Lombard"

Any other cheat codes i can use.

BTW: This same live cd boots my iMac DV with no issues. Cool!

EDIT: Oh crumb! Feel free to move this to the LiveCD thread which i just now noticed. Sorry!

---

### Post by secundar on 2005-05-12
(bump) anyone? ](*,)

---

### Post by Len on 2005-05-12
Seems like a faulty Xorg configuration. The configuration file is stored in /etc/X11/xorg.conf .

I'm afraid there isn't a way to fix it with the LiveCD, you'll have to install Ubuntu on your disk and manually adapt your xorg.conf file. With a little luck another forum member has the same machine and will post the config for it.

Since the CD uses the same autoprobing as the installation program on the HD will do the HD installation will have the same problem. You can switch to a terminal with control+alt+F2 (not sure... I haven't GDM running here) where you can type commands and fix this. ```
nano -w /etc/X11/xorg.conf
``` will open a text editor with the Xorg configuration file. Use google or the man pages to get info about this topic.

Sorry for this to sound complicated. Hopefully someone will post the right configuration so you do not have to do anything :).

---

