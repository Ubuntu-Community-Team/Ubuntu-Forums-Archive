---
title: "Smooth Kubuntu 7.04 install, but no KDE desktop. Did I mess up??"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-09
Just downloaded the Kubuntu 7.04 iso, burned image to disc and installed the OS without a hitch, (dual boot with XP--for now). Only problem is when I boot up I get the gnome desktop with no selection in options on the log in screen for KDE (which is, I assume the Kubuntu desktop). Do I have to download the KDE desktop seperately, or is it installed automatically with the OS and I just don't know where to look ?? Thanks for the help in advance.

---

### Post by tgm4883 on 2007-07-09
Hmm, you shouldn't have the gnome desktop.  Are you sure you downloaded kubuntu?  Where did you download it from?

---

### Post by RomeReactor on 2007-07-09
Hi. If you get the Gnome desktop after booting up, then you installed Ubuntu, not Kubuntu; you can get the KDE environment and applications from Synaptic (search for **kubuntu-desktop**). Or, from the command line:
```
sudo aptitude install kubuntu-desktop
```
after the installation finishes, you get the option to choose your desktop environment at the log in screen. If the installation goes fine (though there's no reason it shouldn't) and you want to remove Gnome (because you have limited HD space, etc.), take a look at [this page]("http://www.psychocats.net/ubuntu/purekde").

---

