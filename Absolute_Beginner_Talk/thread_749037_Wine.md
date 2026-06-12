---
title: "Wine"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by noskillz on 2008-04-08
I ran wine to install a program, and it installed correctly, but I'm not sure where it went. It didn't install any buttons of itself and I can't find the path it is in to run it through terminal. How can I find it?

---

### Post by canthus13 on 2008-04-08
It should show up under the Wine entry in your applications menu.  Go to Wine -> Program Files -> Yourprogramhere.  If it's not there, check out the .wine/drive_c/Program Files/ directory in your home folder.

--Me

---

### Post by warbread on 2008-04-08
First, if you haven't already, you'll want to run 'sudo winecfg' and then hit the 'scan' button in the 'drives' tab.  When it's configured, you should have a Wine folder in the Main Menu and your program may be there.  If not, you can find everything in ~/.wine/drive_c/

From there, it's like looking at a normal Windows install.

---

### Post by ramjet_1953 on 2008-04-08
Don't forget that when WINE installs, it does so in a hidden directory under your home directory.

When you open Nautilus, just click on [COLOR="Blue"]view[/COLOR] and put a tick in [COLOR="Blue"]Show Hidden Files[/COLOR].

Now navigate to [COLOR="Blue"]/home/.wine/drive_c/Program Files/[/COLOR]

You should now be able to see all of the Windows programs that you have installed using WINE.

Regards,
Roger :cool:

---

### Post by Tyke91 on 2008-04-11
also, if you are using a later version of wine, go to System>Preferences>Main Menu and activate the wine menu button so that your wine apps will be accessible thru the Applications menu.

---

