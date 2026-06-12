---
title: "subseven???"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by neewby on 2006-08-06
I have many attacke from source ip : 10.0.0.2 service backdoor-g/subseven

IS this any good???

---

### Post by NyTE on 2006-08-06
I doubt you have a trojan on your ubuntu Install...

Unless you have it on Wine maybe?:-k

---

### Post by neewby on 2006-08-06
what is 10.0.0.2 IP source ???

---

### Post by halitech on 2006-08-06
10.0.0.2 would be the IP address of the machine sending you the attack. Do you have a router and if so, do you have a windows computer with that IP?

---

### Post by neewby on 2006-08-06
I have vmware with knoppix std bridged connection

---

### Post by stimpack on 2006-08-06
10.0.0.2 is a machine on your network either your own machine or someone leeching your wireless. subseven is a windows trojan that was very popular back in the day.

I would find out what machine 10.0.0.2 is and sort it out.

---

### Post by halitech on 2006-08-06
another possiblity is if your ISP assigns 10.0.0.x IPs to save on real ones and then uses NAT to give you a routable IP when you request a website, that it may be someone in your area that is trying to get in using subseven. Do you have a wireless router/connection?

---

### Post by neewby on 2006-08-06
bridged connection on vmware

I ran a few scan from guest machine to host

maybe that was it

---

