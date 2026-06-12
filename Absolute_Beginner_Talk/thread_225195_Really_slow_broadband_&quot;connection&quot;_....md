---
title: "Really slow broadband &quot;connection&quot; ..."
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-07-29
Hi all,
I use a ADSL modem for broadband..does not have a static IP address..
Heres the big problem:
Waking up after stand-by..the connection takes an awfully lot of time to connect (find the IP address.)..almost 3 minutes! This problem doesnt occur in windows..I have also observed this problem on other laptops running ubuntu..
Not only that..but if the ethernet cable has been removed..and then inserted back again..it takes the same time to start send/recieving packets..
What should i do to enable the OS to start send/recv packets as soon as the cable has been connected?

---

### Post by Apple 101 on 2006-07-29
You could try restarting your network card interface in Network Manager after leaving stand-by mode.

---

### Post by PaulFXH on 2006-07-29
Hi
I had the same problem and solved it by disabling the ipv6 option in FireFox (this is the default)

In the FF address bar, type about:config
You will then see an optional filter box - enter ipv6

Set network.dns.disableIPv6 to True and restart Firefox. 

Good luck
Paul

---

### Post by kitt on 2006-07-29
> **Apple 101 said:**
> You could try restarting your network card interface in Network Manager after leaving stand-by mode.

ive done that..doesnt help..
And disabled ipv6 and all that...

I really want a fix to this problem because it is very annoying..imagine waiting for 3 mins to connect to the internet..looking at the 'connected' networkmanager applet..heck, even ol' dialup connects faster..

---

