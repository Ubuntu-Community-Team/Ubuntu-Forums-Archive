---
title: "why am i not recieving dhcp when enabled?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by mosedavid on 2006-12-20
this seams to be quite a common problem but i havent found the answer yet after trawling google and here so..

I have a wireless nic which shows up, driver installed (ra2500).  I can see the wireless router which is connected to a ADSL modem/router.  The modem sends out dhcp to the other pcs which get their ip addresses but my wireless nic doesn't pick anything up.

it shows as connected, full signal strengh.  correct wep key inserted, correct essid inserted but i still cant get an ip address, ping out etc.

i have long hair at the moment, i think i may be soon bald with frustration if i cant get this to work.

---

### Post by mosedavid on 2006-12-20
dont quite understand what is going on here.. I now have it working but i cant use any WEP encryption or it doesnt work.

My wireless access point was set up to just be that - a wireless access point on a 3 machine lan.  I now have it set as a dhcp server - the laptop works with this whereas it wouldn't receive one from the ADSL router.  The ADSL router is also setup to be a DHCP server.  Under windows i didn't have to change my wireless settings and i could use full encryption and mac addressing.  This is the only linux pc on the network and I'm concerned about security implications of an unsecured wireless hub - unauthoriesed access to my broadband and windows machines.

The DHCP setup includes a 'DNS' setting -  I have put the ADSl router's IP in this place and i can connect to the internet, ping etc.

Have I missed something in the hub's setup or is it that the driver that Ubuntu has loaded for me is rubbish?

I really want to like this OS but after 4 hours of frustration im running out of ideas.

---

