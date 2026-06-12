---
title: "Problem with ISP connection"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Jimpdx on 2007-08-01
Hello!  In the last few days, I've been having trouble getting online when I boot Ubuntu 7.04 from GRUB.  If I boot Windows first, then press the restart button on my machine,  I'm connected!  Otherwise, I'm not.  I've checked my network settings carefully and everything seems to be copasetic.  I contacted my ISP, and was told that the problem is with the dual-boot setup, but no solution was offered.

Any and all help is appreciated.

---

### Post by sad_iq on 2007-08-01
Do you use dialup? What moem/router do you have?? We can't help without knowing more stuff. Please post the model/brand of your modem/router. Also are you using static Ip or dinamic? (between the router and Pc if a router exists)?

---

### Post by Jimpdx on 2007-08-01
DSL, static IP address.  I have a direct connection to my ISP, no proxies.  I have no difficulties connecting from XP, but I prefer Ubuntu/Linux for the tighter security.  I don't believe that my Cisco ADSL "modem" is the issue.  The problem seemed to coincide with the new version of iptables.  I tried uninstalling Firestarter, but that didn't help.

Thank you for the response.

---

### Post by sad_iq on 2007-08-01
The modem is it usb?? Does ubuntu sees it??? (maybe an update removed something?? maybe you have???) I kinda don't have any experience with modems(had an usb one..made it work after 3 weeks..threw it away and bought a router). Also post the model of the modem...maybe it has a known bug or something!!! Could you also post the output of this command ```
ifconfig -a
```

---

