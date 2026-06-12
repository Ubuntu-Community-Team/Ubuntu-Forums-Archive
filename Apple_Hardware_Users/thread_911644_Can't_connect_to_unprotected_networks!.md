---
title: "Can't connect to unprotected networks!"
date: 2008-09-05
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-09-05
I can't connect to UNprotected wireless networks using the ath9k drivers. I've tried with nm and wicd. I can however connect to unprotected networks using ndiswrapper, but then I can't connect to protected networks!

Help :(

---

### Post by Qloor on 2008-09-06
Have you tried opening Network-Manager's Wireless connection preferences and setting the password type to WPA Personal and simply not entering a password?

System -> Administration -> Network -> Unlock -> Wireless Connection -> Properties -> uncheck Roaming Mode -> select your network -> set Password type to WPA Personal -> keep Network password blank -> set Configuration to Automatic configuration (DHCP) -> click OK.

---

