---
title: "How to make an icon/program for modem"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by Henrythewound on 2006-05-12
Hey there, I'm not sure what the proper term is, but my goal is to create an icon or something on my desktop that will dial my internet connection (yes still suffering w/ 56k :-| ). I am running the Gnome Ubuntu desktop, I believe its the 12.10 kernel update if it matters. Currently I have to go to the drop down Administration menu, choose networking, and click "activate" on my modem device. I then have to do all this again when i'm finished tying up my phone line. Is there any way to make this a bit more automated/convenient? I appreciate any tips!

Wound

PS - I configured wvdial but when I try to run it from the terminal it never dials, I hear the dialtone, but it never dials out. There is probably some line I can add or comment out in wvdial.conf, but I am not aware of it.

---

### Post by Clay85 on 2006-05-12
Well you can create a desktop icon with the launcher (right click the destkop and select create launcher) and put 
```
gksudo network-admin
```
for the command. But this only brings up the window you're finding in the Menu. Is that what you wanted?

Edit: lol there's a much easier way. Go to your Menu, click System, administration, right click networking and select add this launcher to destkop. You even get a cool icon.

---

### Post by Henrythewound on 2006-05-12
Sweet, I'll do this tonight. I suppose you can make one of these launchers for just about anything you like huh? I'll have to play around with it. Thanks for the reply, this should do exactly what my lazy side demands.

Wound

---

