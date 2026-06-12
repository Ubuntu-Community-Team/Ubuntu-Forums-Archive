---
title: "ltsp question: monitoring process"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ollenotna on 2007-07-19
I've installed edubuntu 6.06 to set up an ltsp system

When thin-clients boot they get an ip from dhcp correctly, the ubuntu splash screen appears on thin-clients monitor with usual msgs:
installing essential drivers.....ok
mounting root filesystem......ok
then the screen blanks, leaving a blinking cursor on the top left corner.

I really did nothing on the server: just standard installation, as edubuntu is said to give ltsp out-of-the-box.

So I tried to check the process on the server: some time ago I tried k12ltsp - an environment based on fedora, and to do this I used
tail -f /var/log/messages 
this gave me all the information about thinclients connections, ip, x server and so on.
But in ubuntu this cmd doesn't give me any message about dhcp and thin clients.
How can I control the system during the ltsp booting process?

tia
Antonello

---

