---
title: "Azureus Problems"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by panthro10 on 2007-02-07
I am having some problems setting up azureus. I have been using ubuntu for a couple of days now. I installed 6.10. I have a DSL line with a router. My roomate has a mac, and we access the a wireless network via an airport. I have installed azureus, and it runs fine. I have forwarded ports through my router, i set one port for the mac (62000)  and another port for my laptop (62001). I believe I did this correctly. However, I cannot upload from my laptop that is running ubuntu, and download speeds are very slow. right now azureus claims that nat is ok, and dht is firewalled. does anyone have any advice? I have become familiar with azureus, but would I be better off switching to another client? oh yeah, I tried for a while to set a static ip address for my laptop with ubuntu, but everytime I did i could not access the internet..

---

### Post by rai4shu2 on 2007-02-07
Your DHT is firewalled?

---

### Post by panthro10 on 2007-02-07
yes.. the icon at the bottom is yellow and says DHT firewalled. I do not have a firewall set up, and I thought the port forwarding would take care of that.. but apparently it is not working..

---

### Post by dcclabough on 2007-02-16
You should check to see if you have firestarter... if so, then you will need to open those same ports again...
try typing: "sudo firetarter" in the command line... if firestarter starts, then that is your problem

---

