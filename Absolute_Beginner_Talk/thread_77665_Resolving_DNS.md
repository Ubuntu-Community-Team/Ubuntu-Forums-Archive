---
title: "Resolving DNS"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by Stringent on 2005-10-17
Hiya,

Just installed the latest release 5.1. I am having some problems resolving servers on our LAN. We have DNS setup and my Ethernet card is set to get an IP address from the server. It picks up an IP and gets the DNS name servers, but fails to resolve name -> IP. I can get the computer I need from an IP address, but realistically I don't want to do that. 

I added a couple of PCs to the host file, but its still not resolving. Any other ideas?

---

### Post by soonindallas on 2005-10-17
are the other computers windows boxes ?  if so their netbios names cannot be used by utilities like ping.

you can use netbios names in samba to connect to win boxes' shares or printers.

---

### Post by Stringent on 2005-10-17
Yes they are Windows Boxes. How would that work if I needed to connect to one of the internal intranet webpages via FireFox?

---

