---
title: "I have no /etc/X11 in dapper"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by BLTicklemonster on 2006-12-26
I am having some problems here. For some reason, there's no X11 in my /etc/ directory. 


Anyone have any idea what I can do to remedy this? I have no idea how it went to missing. I couldn't even tell you what caused it. One day dapper is working fine, And I usually use feisty or edgy on another drive, but now I've booted to dapper, and my sessions are all messed up. I tried to see what was causing this, and lo and behold, there's no /etc/X11/ anymore. 

Quite odd.


*edit:

Okay, sudo dpkg-reconfigure xserver-xorg got X11 back for me, but still, when I log in, I don't show all the window managers I ought to be showing, even though everything appears as it ought to be in X11 and /usr/"places things go".

Is there anyway to manipulate what I see in sessions when I am booting?

---

### Post by BLTicklemonster on 2006-12-26
Let me see if I can make this a bit more plain.


When you have like gnome, kde, xfce, icewm, and other window managers installed, you ought to be able to change sessions on the login menu. I can't. I don't even have the option to chose gnome. Just failsafe gnome and a couple of other ones, but none of the above. IF I put fluxbox in .xsession in /home/bill, then I boot directly to fluxbox. If I remove xsession from /home/bill, then I boot to gnome.

Where did all my other sessions go to?

---

