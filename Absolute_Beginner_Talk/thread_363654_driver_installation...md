---
title: "driver installation.."
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by d_maniger06 on 2007-02-17
good day!

i posted a query on how to connect to the internet in my ubuntu a couple of days ago..thanx to all who tried to help but i havent work it out..i have a question now that may help me solve my problem for internet connection..

my router is connected to my computer through a USB cable..now, before i can connect to the internet in my windows xp, i need to install a driver of my router..ive tried to insert my cd driver in ubuntu but i jst opened it..my question is how can i install the driver into ubuntu?..i believe installing things in ubuntu is not the same with windows..so can you guys help me please?..

thanx for always..

God bless!

---

### Post by jure1873 on 2007-02-17
unplug your modem, open a terminal and type in sudo tail -f /var/log/messages and then plug back the modem in and post here what gets printed in the terminal window. What kind of modem do you have? is it supported under linux?

---

### Post by d_maniger06 on 2007-02-17
ive typed sudo tail -f /var/log/messages and this what came out..

> 
Feb 17 22:35:52 JesusZone gconfd (ranran-3994): Resolved address "xml: readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

Feb 17 22:35:52 JesusZone gconfd (ranran-3994): Resolved address "xml: readwrite:/home/ranran/.gconf" to a writeable configuration source at position 1

Feb 17 22:35:52 JesusZone gconfd (ranran-3994): Resolved address "xml: readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

Feb 17 22:35:52 JesusZone gconfd (ranran-3994): Resolved address "xml: readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3

Feb 17 22:35:52 JesusZone gconfd (ranran-3994): Resolved address "xml: readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

Feb 17 22:35:56 JesusZone kernel: [  99.519555] Net: Registered protocol family 10

Feb 17 22:35:56 JesusZone kernel: [  99.520036] lo: Disabled Privacy Extensions

Feb 17 22:35:56 JesusZone kernel: [  99.520571] IPv6 over IPv4 tunneling driver

Feb 17 22:36:09 JesusZone gconfd (ranran-3994): Resolved address "xml:readwrite:/home/ranran/.gconf" to a writeable configuration source at position 0

Feb 17 22:37:03 JesusZone kernel: [  166.789720] usb 2-2: USB disconnect, address 2



---

### Post by jure1873 on 2007-02-17
it's strange that there is a "USB disconnect" message but not something like "new full speed USB device using..." so I could figure out if the modem get's recognized. Did you plug in the modem before typing that into the terminal?

---

### Post by d_maniger06 on 2007-02-17
ya..i forgot to disconnect it..but after the first time, i exited the terminal and opened it again and typed it in again, and the same thing displayed..

---

