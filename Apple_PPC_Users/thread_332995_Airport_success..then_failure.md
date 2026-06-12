---
title: "Airport success..then failure"
date: 2007-01-06
forum: Apple PPC Users
---

### Post by gamgee911 on 2007-01-06
Ok, I followed the instructions on [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy) and my airport worked through the network manager.  Then I restarted and it didn't work anymore :mad: 
I retried the instructions but it doesn't work anymore.  Anybody got some input if I did something wrong or missed something?  thanks.

---

### Post by Rackerz on 2007-01-06
You need to make sure the modules load at boot time, I can't remember exactly how to do it but I'm pretty sure that's problem.

---

### Post by gamgee911 on 2007-01-06
yeah i kinda figured that might be the problem, does anybody know how to load them at boot time?

---

### Post by gamgee911 on 2007-01-06
ok, i played around and deleted the created firmware in the lib/firmware/2.6.17-10-powerpc/ folder  then i redid the bcm43xx-fwcutter extraction and rebooted.  Now my wireless works but not with the Network Manager, it says "No Network Connection" and "No Network devices have been found."  so my wireless works, it just doesn't show up in network manager.

---

