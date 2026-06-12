---
title: "Accessing internet from Firefox (dial-up not working)"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by trav1085 on 2006-01-02
I can connect to the internet with "sudo pon internet" or use minicom, but when I'm connected I go to Firefox and go to Google.ca but it says that the page can't be found, I know that means i'm not connected to the internet but I do hear the static sound for the dial-up

Is there some way to make firefox automaticly dial-up when I open it? Like IE has the option to connect when opening instead of having to use terminal or manually connect.

I can also download anything needed to make it work, I just save it to my memory then restart into linux

---

### Post by d1337 on 2006-01-02
Sounds like you are already there.  If pon is working and the modem is dialing/you're hearing static it sounds as if you are likely already connected and have some other issues.  Are you able to ping something from a terminal?
```
ping www.google.ca
PING www.l.google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=239 time=34.6 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=239 time=34.5 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=239 time=34.8 ms
```

d1337

---

### Post by TeeAhr1 on 2006-01-03
It may be Firefox.  Check this out: in the address bar, type about:config -- this will bring you a great big page of config options.

In the "filter" bar at the top of the page, type "ipv6"  This will filter all the available options out and leave you with something that says "network.dns.disableIPv6"  If this setting says "false," right-click on it and select "toggle."  It should now say "true."  

Try connecting to google again.  I had the same problem out of the box, and this cleared it right up for me.     -p.

---

