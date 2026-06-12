---
title: "[SOLVED] Password not accepted  - but it is in the command line"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by JGT on 2007-10-24
Hi

I'm having myriad problems upgrading, but I've finally done it - I think!

One new problem! I can log in at the command line no problem, but when I log in through the GUI at start up, the screen turns black for a second then I'm back where I was, i.e. it asks me again! Any solutions?

Many thanks.

John

---

### Post by aysiu on 2007-10-24
Can you try logging in at the command line and typing ```
sudo apt-get clean
``` and then logging in at the GUI again?

---

### Post by JGT on 2007-10-24
Bit weird. I tried what you said, and also upgraded again from the command line just to be sure.

I've got Kubuntu installed too. The loading screen shows "Kubuntu", but when I log in, if I choose Kubuntu, I'm stuck at a terminal in the GUI. (I can't minimise it and there's no other icons).

Choosing GNOME works. Lot of KDE stuff on the GNOME menus but, if I leave them alone, I'm alright. Restarting displays "Kubuntu" too!

At least I'm in - many thanks.

---

### Post by aysiu on 2007-10-24
Maybe try logging into Gnome, pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
mv ~/.kde ~/.kde.backup
``` and then logging into KDE again.

---

### Post by JGT on 2007-10-24
Many thanks. I can log in and out of KDE and Gnome now.

God bless!

Bye

John

---

### Post by aysiu on 2007-10-24
Just so you know, the command I gave you renamed the KDE personal settings folder so that you'd get a fresh set of personal settings. The fact that the command worked means you had some kind of corrupt settings (I don't know how it got corrupted, though).

---

