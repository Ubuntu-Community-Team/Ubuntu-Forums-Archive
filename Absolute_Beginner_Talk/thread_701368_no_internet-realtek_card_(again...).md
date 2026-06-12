---
title: "no internet-realtek card (again...)"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2008-02-19
I have a realtek RTL8168/8111 and run a dual-boot system (XP & Ubuntu 7.10). Internet is fine in XP, but doesn't work in Ubuntu. 
At first, the Wake-On-Lan-After-Shutdown enabling worked, but, after rebooting, my connection got lost. I must say that I didn't open Windows again, so maybe it's not their fault.
The whole shutdown-unplug thing that is supposed to work, doesn't. So, I don't know what to do and would really appreciate any help you can give me...

P.S. I entered my BIOS setup and the Onboard LAN Boot ROM is disabled, does it have anything to do with my problem? (although I did enable it once and nothing changed...)

Thanks in advance...

---

### Post by spudratic on 2008-02-19
had the same problem boot into windows go to control panel system device manager find the nic card and show the properties on one of the tabs there should be a option to keep the card enabled after shutdown click it and the boot into ubuntu and it should work> it did for me.this is a problem in ubuntu with the driver it uses it can't turn on the card in dual boot systems for some reason or another I forget been trying to fix so much in this operating system that my brain can only hold so much lol

---

### Post by spudratic on 2008-02-19
Also I would reinstall ubuntu again after you do this it will check for updates on install I think .I did this just to be safe the install does not take that much time compared to windows

---

### Post by christina_svats on 2008-02-19
Thanks for the reply...I  have already tried this but no luck...
I am not sure it's a windows thing anymore, something else must be wrong...
I also tried some stuff I found about realtek drivers for linux but no solution there either...

---

