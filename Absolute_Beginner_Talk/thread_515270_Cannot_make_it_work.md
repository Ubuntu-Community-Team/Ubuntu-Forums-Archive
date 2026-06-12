---
title: "Cannot make it work"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by eddugo on 2007-08-01
I have just installed 7.04 in a dual boot config on a windows XP machine.  It will not connect to the internet when booted in Ubuntu, but works fine in the Windows boot.  The modem is an ADSL by Embarq, the router - Linksys.  I have tried the basic install - doesn't work.  I have also tried Applications/Accessories/Terminal and ran sudo pppoeconf.  This finds one ethernet devise, but can't find an ISP concentrator.  The message says "Another reason for the scan failure may also be another pppoe process which controls the modem"
Can anyone tell me what to do next?  Thank you in advance for your response.

Ed

---

### Post by apswartz on 2007-08-01
If you are using a router you don't need pppoe to connect. Just configure your network connection as a LAN.

---

### Post by init1 on 2007-08-01
> **eddugo said:**
> I have just installed 7.04 in a dual boot config on a windows XP machine.  It will not connect to the internet when booted in Ubuntu, but works fine in the Windows boot.  The modem is an ADSL by Embarq, the router - Linksys.  I have tried the basic install - doesn't work.  I have also tried Applications/Accessories/Terminal and ran sudo pppoeconf.  This finds one ethernet devise, but can't find an ISP concentrator.  The message says "Another reason for the scan failure may also be another pppoe process which controls the modem"
Can anyone tell me what to do next?  Thank you in advance for your response.

Ed
I am confused. You are trying to connect with ethernet, right? Try a 
```

sudo dhcpd eth0 -t 10
firefox

```
in the terminal. That might work.

---

### Post by init1 on 2007-08-01
> **apswartz said:**
> If you are using a router you don't need pppoe to connect. Just configure your network connection as a LAN.
That's what I was thinking. PPP is for dial up.

---

### Post by eddugo on 2007-08-01
I'm so new to Ubuntu that I don't know where to do that.  Can you guide me through 
Thank you
Ed

---

### Post by eddugo on 2007-08-01
I would put this command in whrere?
Thank you'

Ed

---

### Post by eddugo on 2007-08-01
I'm lost.  Where would I go to config a LAN?

Thank you

Ed

---

### Post by apswartz on 2007-08-01
I use kubuntu, so I'm not sure of the actual program in ubuntu, but in your settings there should be an option for configuring a network connection. Adjust those settings to connect your eth0 using DHCP.

---

