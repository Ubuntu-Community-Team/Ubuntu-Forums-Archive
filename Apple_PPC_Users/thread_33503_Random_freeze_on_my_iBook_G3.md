---
title: "Random freeze on my iBook G3"
date: 2005-05-11
forum: Apple PPC Users
---

### Post by robg on 2005-05-11
Hello, I use a late model iBook G3 at 900mhz, it has the radeon mobility card. I used to run Debian Sarge on it but decided to try Ubuntu Hoary on it since I use it on all my other desktops now. Overall it worked fantastic, but then it started to crash randomly on me. I still use the default kernel and everything. When I use it it's just a matter of time before it just freezes. Sometimes it happens not long after boot, sometimes after an hour. I have no clue at all what it could be so I hope maybe some people on this forum know about possible known issues here. Since it just freezes I think I cannot post a good bug report. Thanks.

---

### Post by dietrying on 2005-05-11
did you try another kernel image? maybe it is defect?

---

### Post by chascon on 2005-05-11
[QUOTE=][/QUOTE]
 try disabling (#) DRI in /etc/xorg.conf
If this works it is a DRI issue which I have seen before on some Rage 128 cards

You might also want to change the default depth from 16 to 24 or what ever values are supported.

---

### Post by robg on 2005-05-12
[QUOTE=chascon]try disabling (#) DRI in /etc/xorg.conf
If this works it is a DRI issue which I have seen before on some Rage 128 cards

You might also want to change the default depth from 16 to 24 or what ever values are supported.[/QUOTE]

Okay thanks, I'll try this, if it works I'll "report back".
Hoping I will not have to live without DRI alltogether :-).

A new kernel image is not really an option, if the default ubuntu kernel really fails then I should report such a bug, first gotta find out what's the problem.

Thanks.

---

### Post by farruinn on 2005-05-12
The system log may provide you some clues as well (should be /var/log/syslog)

---

