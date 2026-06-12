---
title: "cant get one computer to function in network"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by meddinmonk on 2007-04-21
i just installed ubuntu so i could make a router/server 1 for personal use and 2 for my class project. I got the router to work wonderfully and can almost throw out my linsys router. however one computer in my home shows network cable unplugged.

the setup
cable modem -> router
router -> switch
switch -> comp1, comp2
comp1 runs windows xp 64bit with a NVIDIA nForce Networking controller
comp2 runs windows xp 32bit with a broadcom netXtreme controller

comp1 can get an ipaddress and access the internet from the router i can ssh to the router it works perfectly

comp2 says network cable unplugged. i have unplugged the cable connected to comp2 and plugged it into my laptop which runs windows xp 64bit and it obtained an ip address and accessed the internet and worked perfectly. plugged it back into comp2 and network cable unplugged.

the nic in comp2 works because with the setup
cable modem -> linsys router
linksys router -> comp2

comp2 can pull a signal and get on the internet

i dont know what needs to be checked on why this one computer cant connect. Do i need to install the driver onto the router for the boadcom card? Is broadcom just not linux friendly and i need to buy a nic card specifically for this? 

sorry for the long post and any help would be very appreciated

mm

---

### Post by Albi on 2007-04-21
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

The sticky should resolve it if its anything to do with your ATI card (It's the same procedure for 9*** and X****

---

