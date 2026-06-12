---
title: "Clock synchronisation"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by apette on 2006-01-18
During startup, my computer stops and uses a lot of time on the Clock synchronisation step. What should I do to fix this?

I am using a Compal CL56 computer, Pentium Mobile 1.6GHz processor, 512 mb RAM, 60 GB harddrive, Ethernet card: Realtek 8139; Wirelss: Intel Pro/wireless 2200BG.

---

### Post by apette on 2006-01-18
I guess it's just because I am on the network of my university, and can't access the time server from here.

---

### Post by bscbrit on 2006-01-18
When you try to syncronise the clock are you already connected to the internet i.e. have you got a permanantly on connection?  If it is trying to contact the NTP server but cannot get out it will until each connection attempt times out before continuing.  If you do not use NTP to syncronise your computer clock, then deselect it.

---

