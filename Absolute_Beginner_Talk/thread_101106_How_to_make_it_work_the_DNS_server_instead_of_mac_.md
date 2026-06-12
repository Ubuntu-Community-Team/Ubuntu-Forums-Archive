---
title: "How to make it work the DNS server instead of mac address?"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-12-09
How to make it work the DNS server instead of mac address?

---

### Post by patrick295767 on 2005-12-09
I meant how could I change my IP address to the Hostname of my pc ?
I have a DHCP  for the linux pc's.
I 'd like to have the hostname instead of using the ip address that could change 'cos of DHCP 
...
Sorry for the confusing title of my post (early morning)...
  
Greetz

Pat'

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=patrick295767]I meant how could I change my IP address to the Hostname of my pc ?
I have a DHCP  for the linux pc's.
I 'd like to have the hostname instead of using the ip address that could change 'cos of DHCP 
...
Sorry for the confusing title of my post (early morning)...
  
Greetz

Pat'[/QUOTE]
If it's on your internal network, can you just configure your router to give out the same IP addrs to cards via their MAC addresses?  Or can you use static IPs and add entries to /etc/hosts?  Otherwise, I think you'd have to set up a local DNS server.

---

### Post by patrick295767 on 2005-12-09
I tried all way's .... cannot ... too difficult for me to make my dns server ...
tooo noob 
  
I changed parameters of my routeur : It's workign !!! Works great !! Thank you very much !!

  
Pat'

---

