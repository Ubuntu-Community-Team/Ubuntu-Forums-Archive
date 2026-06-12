---
title: "pppoeconf"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-20
I am running SOOOO SLOW.
after reading several posts here and different links through google, I came upon something mentioning the PPPOECONF file, so I opened it, and THIS is what it said:
 NOT CONNECTED &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;          
          &#9474;                                                          &#9474;          
          &#9474; Sorry, I scanned 1 interface, but the Access             &#9474;          
          &#9474; Concentrator of your provider did not respond. Please    &#9474;          
          &#9474; check your network and modem cables. Another reason      &#9474;          
          &#9474; for the scan failure may also be another running pppoe   &#9474;          
          &#9474; process which controls the modem.                        &#9474;          
          &#9474;                                                          &#9474;          
          &#9474;                                              



What do I do now?

Also, when I try to go in to check my network settings, it says I am not allowed to access the system configuration.....

---

### Post by zvacet on 2007-03-21
system>administration>network setting>highlight your modem>properties>select type of connection you want>chek upper left box>close
Click on DNS and you will see one address and replace it with your nameservers>close
```
pppoeconf
```
If nothing works maybe it is your modem not recognized.What modem do you have?

---

### Post by maccawolf on 2007-03-21
How can I do that in terminal? I am unable to get into system administration networking.

---

### Post by maccawolf on 2007-03-21
P.S. Modem is Motorola SB5100 (not VOIP) and Router is Gigabit EE400r.

---

