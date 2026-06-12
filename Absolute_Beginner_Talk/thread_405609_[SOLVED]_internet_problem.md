---
title: "[SOLVED] internet problem"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-04-10
hi everybody,

ive posted about this problem before though dont seem to be getting anywhere - I cant start my internet without having to type "sudo dhclient" everytime I start my machine.  Once I do, it works perfectly well so my questions are :

1) as I have noticed a few other users with the same problem, does anyone know why this has suddenly started (only a couple of weeks ago)

2) How can I get my machine's internet connection to 'just work' without my having to type dhclient into terminal everytime I start up?

I know there isnt a problem with my hardware (I use a typical broadband modem connected via ethernet), I havent installed anything new in terms of software or hardware (other than the standard updates) so any help would be much appreciated - im still a relative newbie to Ubuntu so layman's terms would be fantastic!! :lolflag: 

by the way - here's a copy of what happens when I type sudo dhclient...

bespin@mike-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.90 -- renewal in 34650 seconds.
bespin@mike-desktop:~$

---

### Post by heimo on 2007-04-10
This is not a real solution, but a suggestion for a workaround. Add dhclient to /etc/rc.local, before "exit". It's a configuration file, that gets executed during boot (just at the end of it).
```
 gksudo gedit /etc/rc.local
```

---

### Post by MikeSz on 2007-04-10
thanks for that - you mean like this?.....ive added it to the end as you can see

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
dhclient
exit 0

---

### Post by heimo on 2007-04-10
Yeah, that should do it. Next time you boot, you'll see if it works. BTW, one thing to do is to disable ipv6 if you haven't already. There are lots of threads about it, so you should find how to do it quite easily.

---

### Post by MikeSz on 2007-04-10
il give that a go - many thanks indeed! :)

---

### Post by MikeSz on 2007-04-10
Many thanks heimo - your tip has worked a treat!! :guitar:

---

