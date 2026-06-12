---
title: "Ubuntu hangs when booting up"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Charlietje on 2007-11-03
hi,

My ubuntu 7.10 worked fine until....
I tried to install ogmrip. I couldn't compile the program because it needed glib2.0.... 
I went to the website and compiled the glib.
I tried to compile the program again, but i needed enca.

With apt-get enca, i installed enca
Then i tried to compile ogmrip again but ubuntu didn't respond, so i needed to shut it down the hard way.

When I tried to restart ubuntu, it hangs after the login.. I get the "waiting circle" but it doesn't go further.

Then i rebooted in "safe mode" and apt-get remove enca, what it did perfectly, but i still can't boot.

I also did a dpkg-reconfigure xserver-xorg, but with no succes.
I don't think that's the problem, because it can start the splash screen...

Any help?

Thanks

---

### Post by snickers295 on 2007-11-03
sounds like its the glib because its the only one that messes with the actual system and GUIs.
at the login screen at the bottom of the screen choose the session to be gnome, not xscript and see what that does.

---

### Post by Charlietje on 2007-11-03
I don't get at the login. it's hanging just before it.

is there a possibility to do it command line, when i start the safe mode?
When i start in safe mode, all is ok, but when i wan to 'startx' i get the same problem

---

### Post by snickers295 on 2007-11-03
sounds like glib even more now.
i don't think theres much i can say unless you know how to remove glib.

---

