---
title: "Help with Wine"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2007-10-21
I was playing around with the wine cfg and I set it up for virtual desktop but set the resulition very low. now when I try to edit the winecfg I cannot get to the apply button so I cant do anything on wine now. Please help

---

### Post by daniel_szollosi-nagy on 2007-10-21
Edit ~/.wine/user.reg (using nano or gedit, or whichever editor you prefer)

Search for [Software\\Wine\\X11 Driver]
Change "Desktop" = "800x600" (or whatever resolution you need)

---

