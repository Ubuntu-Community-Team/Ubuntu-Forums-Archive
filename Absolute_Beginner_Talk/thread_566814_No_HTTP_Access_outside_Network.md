---
title: "No HTTP Access outside Network"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by godsfshrmn on 2007-10-03
I am running Ubuntu server 7.04 behind a router with Apache, MySQL, etc. I am able to access the apache website under the same network with the computer's IP, but when I try to use the other IP (assigned by my net provider), it connects, but isn't able to load anything. I have made sure port 80 is open on the router. I assume there is another port that needs to be open? If it can connect, I don't see why it will not load the pages.

---

### Post by bsharp on 2007-10-03
Yes the port needs to be open, but you also need to make sure that you are telling your router to forward anything coming to your WAN on port 80 to go to the correct LAN ip.  

Also you need to have Apache configured to allow connections from your router and outside IP addresses.

---

### Post by Dr Small on 2007-10-03
Port 80 needs to be opened on the computer hosting the Apache server.
Port 80 also needs to be forwarded by you router to port 80 on the computer that is hosting the Apache webserver.

Then you should be able to access the website via your IP address, and can get a subdomain at Dyndns.org for free, to point to your IP address for you, as a IP masking/forwarding service.

To open port 80 on the machine hosting Apache, open Firestarter (if not installed, enable Universe Repositories and install by 'sudo apt-get install firestarter') and then go to the Policy Tab, go click in Services, and add a rule that enables port 80. Apply Policy, and see if it works.

Dr Small

---

### Post by godsfshrmn on 2007-10-03
> **Dr Small said:**
> Port 80 needs to be opened on the computer hosting the Apache server.
Port 80 also needs to be forwarded by you router to port 80 on the computer that is hosting the Apache webserver.

Then you should be able to access the website via your IP address, and can get a subdomain at Dyndns.org for free, to point to your IP address for you, as a IP masking/forwarding service.

To open port 80 on the machine hosting Apache, open Firestarter (if not installed, enable Universe Repositories and install by 'sudo apt-get install firestarter') and then go to the Policy Tab, go click in Services, and add a rule that enables port 80. Apply Policy, and see if it works.

Dr Small
I have the port forwarded to the correct IP. How do I do that from the command line? I'm not running a GUI.

---

### Post by Dr Small on 2007-10-03
From what this page says:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

You need to try this:
```
$ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

---

### Post by godsfshrmn on 2007-10-03
No luck with adding that. I also tried to use port 8080 incase bellsouth was blocking port 80 but still a timeout.

---

