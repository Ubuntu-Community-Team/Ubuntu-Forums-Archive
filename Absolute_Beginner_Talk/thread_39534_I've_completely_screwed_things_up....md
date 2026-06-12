---
title: "I've completely screwed things up..."
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by Kanephan on 2005-06-05
I somehow deleted 3 files (the only one I can remember is ubuntu desktop) now I'm left with no graphical interface at all. It's all completely text based. I'm new, so I'm not too familiar with the commands. What would be the command to get the ubuntu desktop? or to see recently deleted/uninstalled files?

  ](*,)

---

### Post by mark on 2005-06-05
Try *apt-get update && apt-get dist-upgrade* - if you've got a fairly fast broadband Internet connection, this should work.

Mark

The *dist-* part of the above command line will update *everything* - so make sure you want to do this - otherwise, leave the *dist-* out of it...

Mark

---

### Post by az on 2005-06-05
You mean packages.


Install the ubuntu-deaktop package and it will bring everytihng you are missing.

sudo apt-get install ubuntu-desktop

You should not need to be on the internet.  Everything is ether cached on your hard drive or on the cd...

---

### Post by Kanephan on 2005-06-05
Thanks azz, that seems to have worked. I thought I'd hit a wall when it asked me to insert a disc because I previously tried apt-get install Gnome and it didn't accept the disc I put in..

but it seems all is good now. Thanks a ton!

---

### Post by Kanephan on 2005-06-05
Ok now I've got a new problem. My desktop is bigger than my monitor, resulting in having to scroll around to get to the top and bottom panels. How do I fix this?

---

### Post by Gtaylor on 2005-06-05
Your resolution is set too high for your screen it looks like. You can either edit /etc/X11/xorg.conf or I think there's a graphical config utility in Gnome somewhere that'll let you do it via  GUI. If you go the route of editing xorg.conf, delete the resolutions that you know you can't run and hit CTRL + ALT + BACKSPACE to re-start Gnome. You may then need to do something like:

sudo /etc/init.d/gdm restart

---

### Post by bored2k on 2005-06-05
Easier method: sudo dpkg-reconfigure xserver-xorg . There you can select the maximum resolution for your screen.

---

### Post by Gtaylor on 2005-06-05
Or that :)

---

### Post by jjross on 2005-06-05
system/preferences/screen resolution

---

