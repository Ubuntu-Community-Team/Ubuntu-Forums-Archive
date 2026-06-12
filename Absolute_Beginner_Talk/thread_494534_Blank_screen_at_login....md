---
title: "Blank screen at login..."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by encompass on 2007-07-07
I have been trying to tweak with my session properties and now I have this...
I login and get a brown screen, I can hear the startup sound just fine.  But nothing after that.
BUT when I press control alt backspace for a quick moment I see my background!  I am thrown back to the login...
At this point I try to login and it does jsut fine.  no problems at all.
Any ideas how to debug something like this?  I haven't the foggiest where to start.
I am running compiz fussion.  Otherwise this is a normal system.  The only proprietary driver I have is my wirelesscard which works flawlessly.

---

### Post by pbaumgar on 2007-07-07
> **encompass said:**
> I have been trying to tweak with my session properties and now I have this...
I login and get a brown screen, I can hear the startup sound just fine.  But nothing after that.
BUT when I press control alt backspace for a quick moment I see my background!  I am thrown back to the login...
At this point I try to login and it does jsut fine.  no problems at all.
Any ideas how to debug something like this?  I haven't the foggiest where to start.
I am running compiz fussion.  Otherwise this is a normal system.  The only proprietary driver I have is my wirelesscard which works flawlessly.

So after you login in the second time you get your desktop?

---

### Post by encompass on 2007-07-07
Exactly, but after a reboot I am back to the same story. Weird huh?

---

### Post by Stealth on 2007-07-07
I get the same thing! :X

---

### Post by encompass on 2007-07-07
Heh... You could check this..
I noticed that when I press cntrl alt backspace I get a flash of my background on the screen just before it goes back to gdm.  Do you get that too?
If so... I think this is a bug or some other issue that should really be resolved.

---

### Post by encompass on 2007-07-08
Allrighty!
Try this...
in a hidden folder called .gconf in your home derectory... there is an apps folder...
in that apps folder is a gconf.xml file or something of that nature...
move the file away from your computer...
did that fix the issue?
if not... for heaven sacks put the file back. (I don't know what it does.  But it looks risky to play with.)
Good Luck

---

