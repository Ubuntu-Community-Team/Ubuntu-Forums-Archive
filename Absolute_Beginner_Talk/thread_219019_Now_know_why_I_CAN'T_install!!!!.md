---
title: "Now know why I CAN'T install!!!!"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by alan yeates on 2006-07-19
Having been written off as a dead loss in several forums and by my son who runs several Debian platforms, I was determine to find out why I can't run Synaptic and most things needing a password don't work. Turns out that Easy Ubuntu is still trying to download MSS core fonts - it can't resolve Andale.ttf but continally loops and tries again. I read somewhere that Ubuntu won't allow 2 download tools at once, so this looks to me to be my problem. What do I do? I have to have Times Roman, but not much bothered about any others, though for some reason the fonts appear to come as a package. Killing off the terminal does'nt work, as soon as I go to root again the cycle repeats. Admit I have learnt a lot about Linux in the last few days, but would have liked to do it in my own time. :-k

---

### Post by mattisking on 2006-07-19
You'll need to enable "multiverse" in your repository list for apt-get and synaptic? Do you know how to do this? If universe is already enabled, it's easier..

sudo gedit /etc/apt/sources.list

look for the 2 lines ending in "universe", add a space, and the "multiverse" (without the quotes of course). If the two lines that contain universe begin with a #, remove the #. The # comments out those lines and removing them makes them active. Save, and exit gedit.

Then:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install msttcorefonts

After this is done, then try using Easy Ubuntu to enable whatever feature you were trying to enable. Automatix is another solution that is similar to Easy Ubuntu. A quick search on these forums will point you right at it. Good luck and holler if you need additional help.

---

### Post by T700 on 2006-07-19
Even easier than searching--click on the Automatix link in my sig!

:-)

Paul

---

