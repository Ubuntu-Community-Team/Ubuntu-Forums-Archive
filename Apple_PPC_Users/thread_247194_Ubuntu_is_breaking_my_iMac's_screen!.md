---
title: "Ubuntu is breaking my iMac's screen!"
date: 2006-08-30
forum: Apple PPC Users
---

### Post by Ububurns on 2006-08-30
Ubuntu is leaving permanent marks on my iMac's LCD screen!

It can't find an appropriate resolution for booting up, shutting down, screensaver mode or getting to a non-X, terminal prompt (ie: Ctrl-Alt-F1).

Instead I get weird static patterns, a pink, white or black screen - and some of these patterns are leaving patches on the screen.

Please help, as I'm quite worried about the screen deteriorating further!

---

### Post by avtolle on 2006-08-30
Have you tried, from the terminal, sudo dpkg-reconfigure xserver-xorg and selecting the desired resolution; or manually editing the /etc/X11/xorg.conf file to input the correct Horizontal and Vertical criteria?

---

### Post by mdeltito on 2006-08-30
Well, i too have seen those patterns with a dodgy xorg config. But for this to leave "patches" is unlikely. What do you mean when you say patches? Can you provide an image of this?

---

