---
title: "Question regarding network speed on external NIC for firewall"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by dlk on 2007-03-07
Hello:

I'm trying to set up an Ubuntu machine as a hardware firewall for a small office. We're a non-profit and have zero budget, so Linux/Ubuntu seemed a good way to go.

Since we don't have any funds, I'm commandeering an old, unused Macintosh G4 tower for the firewall machine. That computer has built-in 1GB ethernet which will be the LAN side interface, and I scrounged up an old 10/100 NIC for the external interface.

My question is this -- is using the 10/100 NIC going to make the Internet connection seem slower than normal to my users? Our Internet connection is only a 768k DSL line, which is *way* slower than the networking speed of the NIC, so I figure if there's a bottleneck anywhere, it would happen there. 

Does this make sense?

Thanks in advance,
--d.

---

### Post by Strider on 2007-03-07
Hi,

You are correct regarding where the bottleneck would be - the DSL line.  Your users will not notice any speed difference if you set it to 100MB or use the Gig interface on the external side.

-Mike

---

### Post by dlk on 2007-03-07
Excellent, thanks for the information.

---

