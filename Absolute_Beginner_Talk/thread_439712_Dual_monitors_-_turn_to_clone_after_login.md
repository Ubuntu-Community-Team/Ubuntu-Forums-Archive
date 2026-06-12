---
title: "Dual monitors - turn to clone after login"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by randalotto on 2007-05-10
So I just installed a fresh copy of Feisty Fawn. After using Envy to install fglrx for my X850 GTO2, I tried setting up my dual monitors, following the BigDesktop guide elsewhere on this site. I think I have xorg.conf set up correctly, but it just won't work. 

At the login screen, it behaves like it should. I can move the mouse across the screens, and the one on the right is just blank. However, as soon as I log in, the screen flashes black for a second or two, then the screens come up cloned. 

I really don't know what's going wrong... I have a feeling the xorg.log explains it all, and so I'm hoping someone can decipher it for me....

(see below for xorg.log)

Thanks.

---

### Post by randalotto on 2007-05-13
So no ideas....?

edit: new xorg log:
[http://rafb.net/p/K0vqKR64.html](http://rafb.net/p/K0vqKR64.html)

---

### Post by randalotto on 2007-05-20
Bueller? 

Anyone? Anyone?

---

### Post by randalotto on 2007-06-01
So no one has ANY clue?

---

### Post by LordKelvan on 2008-05-13
Hi:

I am not sure whether you have solved this problem (as your posts are about 1 year old), but I recently encountered this problem and have fixed it.

I am using 8.04 (Hardy Heron) with version 8.47.3 of the fglrx drivers (the closed-source drivers that come from ATI).  I discovered from another post on these forums that you have to go into System->Preferences->"Screen Resolution", and properly set the resolution.  It turns out that this "Screen Resolution" shortcut launches gnome-display-properties.  This program maintains its own configuration file under ~/.gnome2/monitors.xml.  I suspect that that configuration file was being read in after login, causing this clone problem.

With respect to what a proper resolution was, I set it to be the combination of my two resolutions.  For my setup, I have a 20" Dell LCD (1680x1050) and a 19" Samsung LCD (1280x1024), and so I set the resolution in "Screen Resolution" to be 2960x1050.  The 2960 is because 1280+1680=2960, and the 1050 is because it is the max of {1024,1050}.

Hope that helps.

---

