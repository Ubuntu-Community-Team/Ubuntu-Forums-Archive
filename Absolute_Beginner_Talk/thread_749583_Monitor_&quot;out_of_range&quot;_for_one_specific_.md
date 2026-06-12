---
title: "Monitor &quot;out of range&quot; for one specific user"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by peterlauri on 2008-04-08
Hi, I have a few different users. I have a Acer 24 inch monitor that has been working well before. However, now I have experienced that one specific user get the "out of range" message from the monitor and GNOME is not started (or at least doesn't show anything). Might there be some file that still thinks it is in some other mode? Logging in with other users works as normal. /Peter

---

### Post by spiderbatdad on 2008-04-08
check user privileges under system->administration->users and groups

---

### Post by peterlauri on 2008-04-09
> **spiderbatdad said:**
> check user privileges under system->administration->users and groups

I checked that, but both users has the same privileges there. This monitor has worked well before, but just after a trip stopped working for ONE specific user.

Are there any files that are in the home folder then that contains user specific information about what screen resolution etc is being used for a specific user?

---

### Post by flyingbrass on 2008-04-09
Maybe check for /home/problematicuser/.xinitrc (notice the leading dot -- it's a hidden file) and rename it if it exists.  Renaming is better than deleting because renamed files are easily restored while deleted ones are lost in the void.

---

