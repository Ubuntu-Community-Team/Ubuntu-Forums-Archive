---
title: "[SOLVED] Unable to login to gnome, thinks I'm already logged in?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by trooperchix on 2007-12-06
I am a total newbie to this, so commands and everything don't make a bit of sense, so please be patient. I'm tired of giving my money to one of the richest men in the world, so here I am Ubuntu!! 

Ok, here's the scoop... I just received my new Dell 1420N laptop with Feisty installed. I tried to install independently Gnucash, and that failed. I found elsewhere where I could add gnucash (through add programs) and that failed also. I logged out, and attempted to log back in and now I get:

The files that contain your preference settings are currently in use. You might be logged into a session from another computer and the login session is using your preference settings files. You can continue to use the current session, but this might cause temporary problems with the preference settings files. You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session. Do you want to continue? and the option is log out or continue. If I hit logout, I get back to the log in screen (and subsequently if I try to sign in again, I get the same edit) or, if I hit continue, I get the following:

Please contact your system administrator to resolve the following problem: Could not resolve the address "xml:readonly:/etc/gconf/gconf.xml.mandatory" in the configuration file "/etc/gconf/2/path": Failed: Couldn't locate the backend module for 'xml:readonly:etc/gconf/gconf.xml.mandatory"

I'm sure there is a wierd easy fix for this, basically as I understand it, the system thinks I'm logged into my profile already when I am not. I can't wait until I get this down so I can ask more intelligent questions.. Your help would be much appreciated...

---

### Post by Dr Small on 2007-12-06
Have you tried rebooting to see if the problem would correct itself?

---

### Post by trooperchix on 2007-12-06
Yes, I've tried rebooting and I get the same thing.  I'm a total noob here, so please be as specific as you can when helping me please!!  I can't wait until I get this OS down...

---

### Post by Hospadar on 2007-12-06
well probably there are some lockfiles sitting around in your home directory that for whatever mysterious reason didn't get deleted at some point.

you should try, when you get to the login screen ctrl-alt-F1 and see if you can log into a text terminal. If you can, get back to your graphical shell (ctrl-alt-F7) and see if you can login, if not, (or if you couldn't even log into the text terminal) then I think the thing to do would be to boot off a livecd, go into your hardrive, locate your home directory, and start rooting around for lockfiles to delete, also if gnucash somehow caused the problem, maybe deleting any preference files it may have created might help.

Make sure you have "view hidden files" turned on, and delete anything in your home folder named gnucash or .gnucash or anything like that, also look for files with "lock" or "lockfile" prominent in their names.

You may want to simply rename these files instead of deleting them, in case you have problems later and need to swap the files back in.

Let me know what you find!

---

