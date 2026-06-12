---
title: "could not connect to (ipaddress) - no route to host"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ahounsome on 2008-02-16
sudo apt-get update not working - reports could not connect to (ipaddress) no route to host. Using a wireless home connection. IP address indicated does not correspond to host name.

---

### Post by Linux_Man on 2008-02-16
Sounds like a router/firewall connection problem to me. Have you tried a different mirror to see if that fixes it?

---

### Post by ahounsome on 2008-02-16
Sorry, I don't know how to do that!

---

### Post by Linux_Man on 2008-02-16
Open Synaptic then Settings ----> Repositories then click on the download from drop-down list and select a different mirror. Other then that, are you sure that you don't have a firewall running either on your router or your computer?

---

### Post by ahounsome on 2008-02-16
Thanks for your quick reply. I can't install synaptic using Adept Manger\installer - wont connect. Normal http requests via firefox work ok, no problem web browsing, It just seems to be calls for updates etc via ubuntu go out via an IP of 192.168.6.2:3128 which is clearly wrong.

---

### Post by upsfeup on 2008-04-23
Bumping this up. I'm having the same problem and having trouble to solve it!

Edit: Solved. I had a proxy set in some obscure config file and didn't remember. The proxy for updates should be easier to reach!

---

