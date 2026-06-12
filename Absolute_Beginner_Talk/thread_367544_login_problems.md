---
title: "login problems"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by SSamiK on 2007-02-22
I think I've might have borked my session, or my window manager or something. Not quite sure what the problem is..other than that it happend when removing Compiz from my system. 
When trying to log in with my default session everyting is dead slow, and eventually hangs without even loading the wallpaper. To get a working desktop I'll have to login with Gnome Failsafe, and start metacity manually.  

Any tips on what might have gone wrong, and how to fix it?

---

### Post by Ben Sprinkle on 2007-02-22
Try logging in this way.
Bootup, then at the gdm press CTRL+ALT+F2. (I think)
See if it's as slow with a terminal login.

---

### Post by SSamiK on 2007-02-22
No problems or speed issues when logging into terminal, only when starting a session. It seems metacity tries to start two times in my default session, witch I'd suspect would cause a problem, and needs to be startet manually in "failsafe gnome"

Installed and uninstalled both Beryl and Compiz (had both working, and completly removed befor trying the other) prior to this happening, so it might be a better solution just to reinstall. :)

---

### Post by Ben Sprinkle on 2007-02-22
After that, go to System > Admin > sessions.
Look in startup to see if it is being started twice. (Might not be in admin, maybe prefrences)

---

### Post by SSamiK on 2007-02-22
it's in preferences. :-)
But no, not in there twice....

---

### Post by taurus on 2007-02-22
Remove the **Default** session.

---

### Post by SSamiK on 2007-02-22
How do i do that?  :-p

---

### Post by taurus on 2007-02-22
System -> Preferences -> Sessions -> Default.  Then, highlight and delete it.

---

### Post by SSamiK on 2007-02-22
hmm... You sure it's the same in feisty? 
Can't see Default, or the name of any other sessions..
In the sessions menu i've got:
Startup Programs, Current Session and Session Options

---

