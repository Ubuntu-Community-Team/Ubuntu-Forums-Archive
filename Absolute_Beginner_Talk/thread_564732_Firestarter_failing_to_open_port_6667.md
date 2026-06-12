---
title: "Firestarter failing to open port 6667"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-10-01
I setup a IRCd, and wanted to open port 6667 in Firestarter so the service could be accessible across my network, by accessing my IP in an IRC client on port 6667.

However, firestarter claims that port 6667 is open as a  service, for Ircd. The Policy has been applied numerous times, and yet I still can not access my ip from another machine on port 6667.

How can I actually get Firestarter to work properly? It works fine for other ports that I have open, such as port 80 and 22. Why will it not accept port 6667 ?

Dr Small

---

### Post by nowshining on 2007-10-02
u could try another and if 6667 will not open, again the best way is to just use another port if u can.

---

### Post by hardyn on 2007-10-02
are you behind a router?

there is no upnp for linux, you must open the NAT ports manually.

---

### Post by Dr Small on 2007-10-03
I am infact behind a router, but I have set the router to forward port 6667 as a public port to port 6667 on 192.168.0.16 (my IP).

This works for port 80, 22 and such, so I do not understand why port 6667 is not opening on my pc's end. I watch firestarter, and even after port 6667 has been opened, and the policy applied, when I attempt it, it shows it as a blocked connection to port 6667. :|

I may have to find somewhere in the IRCd as to where to change the port number.
Thanks guys.

Dr Small

---

