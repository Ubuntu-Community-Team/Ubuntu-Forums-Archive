---
title: "after a week....may switch back to 6.06"
date: 2006-10-31
forum: Apple PPC Users
---

### Post by cmorgan47 on 2006-10-31
so after using 6.10 for about a week, i'm debating switching back to 6.06.  everything works, but some things require a bit of fiddling.  case in point, i have 2 issues left unresolved:

1)  the system clock is crazy.  sometimes it changes on boot, sometimes it doesn't.  sometimes it's off by the timezone, sometimes it's off by an hour or two....probably to do with timezone/DST, but i've tried utc=yes and utc=no with no good results.  this requires me to change the time and fix the sudo timestamp when i boot.  every time i boot.

2)  i have to run dhclient on every boot.  it will then find the router immediately, but nothing i've tried has fixed this.

so they're not that big of a deal, but it is aggravating that these are the exact types of annoyances that drove me to linux in the first place.  i suspect that i can find fixes for them, but i'm getting a little tired of looking and know that within an hour i can be back to a fully functional 6.06.....plus, haven't seen that much of a gain from 6.10 yet.

---

### Post by stmiller on 2006-10-31
Try installing the program sysvconfig to enable/disable startup items. See if that fixes the dhcpd problems. Are you using a wireless connection? Or wired?

And install the ntp server packages to set the clock at boot with a ntp server.

---

### Post by cmorgan47 on 2006-10-31
by sysvconfig, you're talking sysv-rc-conf?  i did install that and i'm pretty sure dhcpd is a startup service....though i had to update it last night to get ethernet tunneling set up for macOnLinux.

and ntp will update once i get an address, but by then i've already had to screw with the time/date to fix the sudo timestamp....probably, if i had an address at boot, it would work though.

will still tinker a bit before deciding, but i haven't seen that much that i need from 6.10 and 6.06 was quite stable.  we'll see.

thanks for the advice.

---

### Post by stream303 on 2006-11-01
I saw some interesting threads in the Gentoo forums about the hardware clock - maybe one of these options might help:

[http://forums.gentoo.org/viewtopic-t-505055.html?sid=e2dd0f667cceccc8b2f5f49c1594ba87](http://forums.gentoo.org/viewtopic-t-505055.html?sid=e2dd0f667cceccc8b2f5f49c1594ba87)

Seems like just booting your OSX install disk once or some open-firmware tricks might settle it down ... maybe... :)

---

