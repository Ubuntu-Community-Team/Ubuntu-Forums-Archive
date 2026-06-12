---
title: "WG511 Cannot find hardware"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by antw on 2006-08-07
Well I have been at this now for two days. I think I have read everything on this forum for the WG511.

I beleive I have a WG511 V1, made in china, and according to the forums I need to use ndiswrapper with the appropiate driver.

I have tried the prism54 driver which sees the card but does not do anything (no lights etc). 

I have tried ndiswrapper with the netgear drivers - no luck.
I have tried ndiswrapper with the mrv8335 drivers - no luck.

Currently ndiswrapper -l is giving me mrv8335 driver present but not hardware present. Device manager is seeing PCi1225 - Intersil isl3890 [Prism GT/Prism Duette] but nothing else. This goes if I remove the card.

Dmesg tells me ndiswrapper version 1.8 loaded but thats it.
IWconfig tells me I have no wireless connections. But if I go back to the prism54 driver it sees it as etho0. (I currently have the prism54 driver blacklisted).

Any ideas?

---

