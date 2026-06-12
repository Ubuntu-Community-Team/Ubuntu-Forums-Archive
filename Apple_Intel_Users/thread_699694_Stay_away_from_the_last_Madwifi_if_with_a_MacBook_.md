---
title: "Stay away from the last Madwifi if with a MacBook Pro 2nd generation"
date: 2008-02-17
forum: Apple Intel Users
---

### Post by GeneralSunTzu on 2008-02-17
Hello,

madwifi issued a new release a few days ago. 
Taking advantage of the fact I had to recompile anyway, because one of the standard Ubuntu update had recompiled the kernel, I innocently thought :"Great, let's install the last release".
Well, if you have a 2nd generation MBP and an Atheros chip set, please don't.
The last release does not work.
Recompiling the previous release, which I always keep on the desktop in case I need to recompile it, got me back to the usual trouble-free WiFi connection (and I have a complex WPA2 Personal network).
Did not have the time to investigate the cause of the mishap, though.
Hopefully somebody else will lte the madwifi people know.

---

### Post by cyberdork33 on 2008-02-17
It is stated in the release notes that it does not support the AR5004 series chipsets. They are rewriting a bunch of code, and this part has not been updated yet.

---

