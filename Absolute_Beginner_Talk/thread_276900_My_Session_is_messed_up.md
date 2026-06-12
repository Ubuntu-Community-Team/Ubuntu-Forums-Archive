---
title: "My Session is messed up"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-10-13
When I start up my session, nautilus, gaim, and a whole bunch of other stuff start by default.  I think I might have accidently checked the "Automatically save changes to sessions" in System>Preferences>Sessions.  However, now I can't get it back to default.  I just want the default stuff - metacity, power manager, volume manager, update notifier, etc...  How would I do this?

---

### Post by GameGod on 2006-10-13
I just did some poking around on my system, and it looks like renaming your "~/.gnome2/session" file to "session.bak" might do it...

(That's the "session" file in the ".gnome2" directory in your home directory...)

---

