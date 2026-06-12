---
title: "can't connect to bellsouth.net"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by blackberry on 2005-09-29
how do i set up for bellsouth.net?can someone help me out please.i would really appreciated if you did.:confused:

---

### Post by cwaldbieser on 2005-09-30
[QUOTE=blackberry]how do i set up for bellsouth.net?can someone help me out please.i would really appreciated if you did.:confused:[/QUOTE]
What kind of service do you have with them?  Is it broadband, or dialup?  The more details you can give about your network, the easier it will be to help you.

---

### Post by grimmson on 2005-09-30
Hello, I have bellsouth (dsl) also. Are you dual booting or swapping between p.c.'s. Dhcp automatically set up my 5.04 pc. I assume when you boot all (three) lights come on? Right now im on a xp machine so I can't tell you what to check. I'll get back to you tomarrow.

---

### Post by grimmson on 2005-10-04
Sorry for not getting back to you quicker. I had system meltdown. Every now and them i can't get on the net even with all lights on the modem lit up. In windows I would have tried ipconfig /release , ipconfig /renew but that doesn't work here. I just figured out if you go to System > Administration > Networking click on deactivate, wait a second and reactivate I can aquire an ip address.  While your there check ethernet connection properties. Make sure your card is enabled and Dhcp is selected, not static (unless your sure you have a static ip.) Once again sorry im so late I'll try to check back soon.:cool:

---

### Post by cwaldbieser on 2005-10-04
[QUOTE=grimmson]Sorry for not getting back to you quicker. I had system meltdown. Every now and them i can't get on the net even with all lights on the modem lit up. In windows I would have tried ipconfig /release , ipconfig /renew but that doesn't work here. I just figured out if you go to System > Administration > Networking click on deactivate, wait a second and reactivate I can aquire an ip address.  While your there check ethernet connection properties. Make sure your card is enabled and Dhcp is selected, not static (unless your sure you have a static ip.) Once again sorry im so late I'll try to check back soon.:cool:[/QUOTE]
From the terminal you can probably just
```

$ sudo dhclient

```
To pick up a new IP address if you like working at the command line.

---

