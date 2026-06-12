---
title: "Newbie woes."
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by psibaboon on 2006-04-08
Hi all. This is my first post in this forum.

 I wish to install K3B on my machine. I'm behind a dial-up connection, so, I can't use Synaptic to do it. I tried to install it using .debs. However, after installing the package, kdelibs-data, my GNOME applications menu went dead. Uninstalling the package didn't help. How do I install K3B the right way?

 Again, Emacs takes up a weird, grayish look on my system (it looks the way xpdf does), instead of the current GNOME theme. Also, XMMS-related windows & menus behave in the same fashion. Can this be fixed?

 Sorry for my bad English.

---

### Post by Ubuntuud on 2006-04-08
The grayish is caused by the root themes (which aren't any). I believe you need to do something like "ln -s ~/.themes /root/.themes" but I do not know it exactly... Hopefully someone else knows.
XMMS menus are another subject, they are created with GTK 1 while the theme you chose is GTK 2. Maybe you should try searching the wiki. Else I'll do it for you, but that could take a while...

---

