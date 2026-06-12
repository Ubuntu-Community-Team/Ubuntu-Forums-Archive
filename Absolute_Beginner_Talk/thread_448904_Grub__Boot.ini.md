---
title: "Grub?  Boot.ini?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Ramthebuffs on 2007-05-19
I had some issues with my boot.ini and when I fixed it I didn't put the name in correctly.  So now when I boot into windows I get a secondary boot menu after grub giving me the option to boot the old "doesn't work" windows or the new one that I created.

This isn't really a big deal, just something I would like to correct.  Should I change grub to find the working XP boot or should I change the XP boot?  I really don't know what I'm doing so a little instruction would be helpful.

Heres the names of my 2 windows boots

Microsoft Windows XP Media Center Edition - this is the one that shows up on grub and loads into a windows dual boot sort of screen

Microsoft Windows XP Media Center - This is the one I created to correct boot issues and works great.

---

### Post by Campingman on 2007-05-19
If you want to remove the listing from the grub boot menu, here is a link to all you needed to know about editing grub options:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
Hope this helps

---

### Post by Happy_Man on 2007-05-19
You want to mess with boot.ini, since it's a Windows menu problem.

---

### Post by Ramthebuffs on 2007-05-19
Pretty easy I just deleted the bad line from my boot.ini

---

