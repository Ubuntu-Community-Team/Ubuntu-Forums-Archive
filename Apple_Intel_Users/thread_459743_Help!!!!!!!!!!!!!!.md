---
title: "Help!!!!!!!!!!!!!!"
date: 2007-05-31
forum: Apple Intel Users
---

### Post by andrewbossie on 2007-05-31
i have a mac book core duo and have been using wireless, easily, for some time now. i recently downloaded google earth and after the install my computer froze, completely. i restarted the computer only to find that my computer doesnt see my wireless connection ne more and when i try to access the network connection icon it gives me a pop-up that says "Please contact your system administrator to resolve the following problem: SIOCGIFFLAGS error: No such device"

Can any one please help me out??

---

### Post by ronocdh on 2007-05-31
> **andrewbossie said:**
> i have a mac book core duo and have been using wireless, easily, for some time now. i recently downloaded google earth and after the install my computer froze, completely. i restarted the computer only to find that my computer doesnt see my wireless connection ne more and when i try to access the network connection icon it gives me a pop-up that says "Please contact your system administrator to resolve the following problem: SIOCGIFFLAGS error: No such device"

Can any one please help me out??
Looks to be a problem with ndiswrapper. I thought that wireless worked out of the box on the Core Duo MacBooks, no? So did you use ndiswrapper?

See [this post]("http://ubuntuforums.org/showthread.php?t=11891") for more info. Hope this gets you started.

---

### Post by ivesjd on 2007-05-31
Wireless does work out of the box with the core duos. Idk why you would use ndiswrapper unless you needed to.

---

### Post by andrewbossie on 2007-05-31
im not using ndiswrapper, or at least i dont think i am

---

### Post by tulula on 2007-05-31
I had that problem after a kernel upgrade last week. What I did was to reinstall the MadWifi driver and got back the wireless connection.

Hope it helps!

FJR

---

### Post by ronocdh on 2007-05-31
> **tulula said:**
> I had that problem after a kernel upgrade last week. What I did was to reinstall the MadWifi driver and got back the wireless connection.

Hope it helps!

FJR
Did you do a kernel update, Andrewbossie? The only change you mentioned was the installation of Google Earth, which shouldn't rock the boat as much as it appears to have done. It's also very possible that you're not using ndiswrapper and your system is just throwing a like error, but have you tried the fixes listed in the post I linked you to? Did they help, or make any difference at all?

If you don't think you're using ndiswrapper, does that mean you're also not using madwifi?

---

### Post by andrewbossie on 2007-06-01
thank you all for you help. i did not use ndiswrapper and i dont think my kernel has been updated but i installed ubuntu over again because there were some other things that i dont think went right during the previous install, so everything is working right now.

---

### Post by ronocdh on 2007-06-01
> **andrewbossie said:**
> thank you all for you help. i did not use ndiswrapper and i dont think my kernel has been updated but i installed ubuntu over again because there were some other things that i dont think went right during the previous install, so everything is working right now.
Very glad to hear it. Post back if you run into any more problems!

---

