---
title: "wireless problems, maybe related to static ip setting?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by sjul on 2008-04-04
Hi!  Thanks for reading this...

I'm having trouble connecting to the wireless network at work.  It detects the network and shows me blue bars in the task pane, but then when i open my browser i get a "server not found" message. 

I've been able to connect to this work network in the past, but I was tinkering with the network settings at home yesterday and I think i screwed something up!   I changed my home setting to Static IP, b/c I was trying to set up samba.  

I can still connect to the wireless network at my home just fine, but at work--nothing!  Please help!  I feel like there must be a straightforward answer, but I don't know what to do.  :confused:

many thanks!

---

### Post by nathansoz on 2008-04-04
Did you try changing your wireless back to DHCP? 

and

Are you able to connect to your work network, just not get an IP address?

---

### Post by bubba_169 on 2008-04-04
Under network settings (system->administration->network) could you save your current settings under the name of 'HOME' or something similar then create another profile for work with DHCP to automatically assign IPs?

---

### Post by nathansoz on 2008-04-04
> **bubba_169 said:**
> Under network settings (system->administration->network) could you save your current settings under the name of 'HOME' or something similar then create another profile for work with DHCP to automatically assign IPs?

Agreed. If ip adressing is your problem here, than this should allow you to connect at both home and work, you would just change the profile.

---

