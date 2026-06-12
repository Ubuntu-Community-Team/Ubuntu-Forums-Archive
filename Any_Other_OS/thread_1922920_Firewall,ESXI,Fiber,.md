---
title: "Firewall,ESXI,Fiber,"
date: 2012-02-09
forum: Any Other OS
---

### Post by Thegmandrive on 2012-02-09
I have a question about some of the different firewall options available.
First let me explain my situation in brief: 
I host my own Ubuntu server at home. I use fail2ban to keep the bruteforcer's at bay. I have just moved to a house and am lucky enough to have a Full Fiber connection. 100mbps up and 100mbps down. Having a little more protection from outside intruders has gone up on my priority list. 

1st question: I have been doing research on Smoothwall, PFsense and Zentyal(Ebox). IDS via snort rules is an important feature. Smoothwall seems to have this built in, and it doesn't seem to take much extra configuration to get PFsense to do the same thing. I was wondering on the communities opinion on these firewalls. I'm leaning toward PFsense. 

2nd question: What is the best way to set up my home network? My idea is to add a second nic to my server (essentially now having 2 nics) Fiber Modem would be connected to nic 1, and a switch would be connected to nic 2. 

The idea would be to create a new VM with PFswitch, that would route traffic to nic 2 (for my internal network) and route the appropriate traffic to a vswitch (which my ubuntu server would be on).

any help or incites would be greatly appreciated. 


**I may just build a little atom box with two nics and have fiber modem connected to nic 1, and a switch connected to nic2 I would then connect my ubuntu server to the switch (just another idea)

---

### Post by Thegmandrive on 2012-05-23
did anyone have any advice?

---

