---
title: "Put in new NIC but it doesn't show up in ifconfig.."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by someonestolecc on 2008-02-07
Hiya,

My onboard network card stopped detecting a cable in it a couple of days ago. I tried re-loading the driver and now I've given up (it drops off the router when the driver starts talking to it, windows xp and ubuntu).

So I put in a new network card, a realtek 8139 I think. It's shown when I do lspci but it does not come up as eth1 in ifconfig ... 

I tried ifconfig eth1 up but of course eth1 doesn't exist... what do I do now if I want to change it's settings/activate it? Or do I need to check if it's really loaded?

---

### Post by raffytaffy on 2008-02-07
Turn of your onboard lan in your bios. Then see if your new nic shows up,

---

### Post by bodycoach2 on 2008-02-08
Start with the easy things: 1. Make sure the plug is all the way in. 2. Try a different wire. 3. Check the plug on the router-switch-hub or modem - make sure it's pushed in all the way. 4. Clean the contacts and reseat the NIC. 

Try the physical stuff before going to configuration.

Geez,....I've watch too many video's on the [OSI model]("http://en.wikipedia.org/wiki/OSI_Model") now!

---

### Post by someonestolecc on 2008-02-08
> **raffytaffy said:**
> Turn of your onboard lan in your bios. Then see if your new nic shows up,

Thanks! I didn't even think of doing that... How would I go about having both cards enabled like as if I just had 2 nics? Great workaround - at least that computer is on the net now :)

---

