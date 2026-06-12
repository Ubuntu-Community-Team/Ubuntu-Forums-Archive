---
title: "Blank Brown Screen on Startup"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by tigerteeth on 2006-07-28
I briefly got Dapper running, but now have problems with startup. I log in with user name and password and it gives me a plain brown screen. The cursor moves, but the screen is completely blank.

I've made a number of modifications to files to fix various things.

To try to fix a wireless 802.11g card, I was told to add to /etc/rc.local

[INDENT]ifdown eth0
ifup   eth0[/INDENT]

Did that.

Then it locked up while booting at "Configuring network interfaces."

To solve that I was told to comment out everything but

[INDENT]auto lo
iface lo inet loopback[/INDENT]

in /etc/network/interface

Did that, but now I have this blank screen problem.

Can anyone help?

---

### Post by shanepardue on 2006-07-28
i had the same problem when i was trying to run breezy, but dapper installed fine...where did you get your dapper cd?

---

### Post by tigerteeth on 2006-07-28
From one of the North American Ubuntu download sites.

---

### Post by shanepardue on 2006-07-28
did you check the cd for defects before installing?

---

### Post by tigerteeth on 2006-07-28
No. I didn't. I'll give that a try.

---

### Post by tigerteeth on 2006-07-28
I did it and it said there were no errors in the checksums, so I guess that's not it.

---

### Post by davebgimp on 2006-07-28
Try undoing the changes you mentioned making, one at a time, reloading the desktop each time and try to see which one is causing the hang-up.

---

### Post by tigerteeth on 2006-07-28
Okay, I'll give that a try. Thanks

---

