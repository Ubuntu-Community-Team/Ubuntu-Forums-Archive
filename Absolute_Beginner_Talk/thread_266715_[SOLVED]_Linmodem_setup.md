---
title: "[SOLVED] Linmodem setup"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by cirorodrigues on 2006-09-27
Hi all,
I got my PCTEL modem working pretty well under Ubuntu 6.06 after some time googling, adjust and installing things. I'm using gnomePPP to dial-up.
But there's some annoying things yet:
1) before use the modem, I'm opening a terminal as root and stopping slamr module, typing "modprobe -r slamr" and restarting it. I learned this is necessary as ungrab-winmodem must be loaded BEFORE slamr, and my system is not doing this way, so I need to unload slamr and load it again, putting it AFTER ungrab-winmodem. QUESTION: how to change this to have slamr automatically loaded AFTER ungrab-winmodem at boot? please give me a very clear direction (what files change, what to insert/delete/change). I found a lot of "change the order of the modules" -- But, sorry, I don't know how to do it :-k .
2) After connect (I can do that), I need to use the terminal to type "route add default ppp0", as I have an active eth0 port and Firefox try to load the webpages from there and not from ppp0. In the networks settings it's possible to determine ppp0 as default (I suppose it's what I'm doing with terminal) but it's possible only when I'm already connected. How to make this route setting persistent?
Thanks in advance.

---

### Post by cirorodrigues on 2006-12-26
solved by the easiest way: I stopped to use dial-up internet...

---

### Post by Sef on 2006-12-26
> solved by the easiest way: I stopped to use dial-up internet...

So you got broadband is what you mean?  (DSL, Cable, Satellite?)

---

### Post by randiroo76073 on 2006-12-26
To set your modem as default go to: main menu-system-administration, click: "Networking".  When window opens highlight your modem, click on "Properties" & under general tab put check in "enable this connection"  Then go to your other network device and take check out of "enable this connection"  That should make your modem the default.
HTH

---

