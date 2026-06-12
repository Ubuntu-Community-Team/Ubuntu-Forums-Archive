---
title: "LiveCD issue, PowerMac G4"
date: 2007-07-04
forum: Apple PPC Users
---

### Post by onefriedrice on 2007-07-04
Computer Specs:
PowerMac G4 2x800Mhz
1.5Mb Ram
GeForce 2MX

Software Installed:
Mac OS X Tiger 10.4.10
Debian 4 (on the same drive)

Problem:
It seems to boot fine from the CD (burned from ubuntu-7.04-desktop-powerpc.iso) and continues right up until it shows the "Ubuntu" thing with the chime.  Then the "Ubuntu" thing goes away, leaving just the cursor and the desktop with nothing else.  Nothing else happens, even after waiting up to 10 minutes.  The computer itself is also quiet (low fan, no hard drive or cd drive usage, etc).

The iso was downloaded correctly and burned at a low speed for quality.  I'm certain the CD is fine.


Has anyone else seen this behavior?

---

### Post by pxwpxw on 2007-07-05
If you can get to a command line terminal and run "top" and look at logs it might tell you what the problem is. I am assuming if you have debian etch installed you have some familiarity with commands.

---

### Post by stmiller on 2007-07-06
Are you getting a blank brown screen? Try this from the PPCFAQs:

> After logging in I get a blank brown screen?

      Sound problems
          o

            Press CTRL+ALT+F1. Log in at the text terminal, if needed. Type
                +

                  killall esd

            and press enter. Press CTRL+ALT+F7 to return to the desktop. Go to Gnome's Sound Prefs and uncheck the 'ESD' box.


---

