---
title: "pmac_zilog/ibook serial modem"
date: 2008-09-25
forum: Apple Hardware Users
---

### Post by BryannPaulaMelvin on 2008-09-25
back in breezy I submitted a bug report. on this modem not working (it worked in 5.04)

supposedly this was fixed in later kernels
It still doesn't work in Hardy now

Researching I find that pmac_zilog in later kernels puts the modem at ttyPZ0 instead of ttys0 as there were conflicts between the 8250 and pmac_zilog

I've run out of ideas except for a custom kernel, and so much has changed since 5.04 I get lost in config :confused:

I have yet to find a way to get gnome kde or wvdial to connect to this modem.

If I NEED to use the modem I'm still using a live 5.04 cd.

Does anyone have a clue how to get kppp wvdial etc to use this modem?

---

