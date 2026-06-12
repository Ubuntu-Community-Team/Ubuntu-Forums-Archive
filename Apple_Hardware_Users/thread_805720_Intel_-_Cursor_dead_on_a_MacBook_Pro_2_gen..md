---
title: "Intel - Cursor dead on a MacBook Pro 2 gen."
date: 2008-05-24
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2008-05-24
After one of the latest updates to Ubuntu HH, my cursor is dead.
I wonder what I should try to fix this.
Probably a safe login, then maybe attempt to disable pommed, and then perhaps editing the xorg.conf files (ultra-dangerous, am rather loath).
Would there be a kind soul who could advice me?
Thank you.

---

### Post by Brightbelt on 2008-05-24
Hi, I had a similar issue; see this thread in which Cyber offered helpful info to safely bring up your terminal without a cursor, which would allow you to edit your /etc/X11/xorg.conf file.
[http://ubuntuforums.org/showthread.php?t=800548](http://ubuntuforums.org/showthread.php?t=800548)

I hope this helps,...Frank B.

---

### Post by GeneralSunTzu on 2008-05-25
Thank you Brightbelt!
The solution was actually even simpler.
As I had installed last btnx, which was supposed to reroute mouse button events, and something had just screwed up, I simply logged on with a Gnome failsafe session (therefore not activating it), removed btnx from the startup  items and then proceeded to an ordinary logon.
I believe the idea behind btnx is very good, its implementation somehow less.
Thank you so much nonetheless!

---

### Post by Brightbelt on 2008-05-26
I'm glad you got it straightened out. ;)

---

