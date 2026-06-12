---
title: "Can Configure two IPs one for outworld and one for lan?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by JoaoCarlosCorreia on 2007-11-06
Hi, 
Can I have two IPs in my machine, one for the internet and one to use in the local network?
If this is possible, just have to add the new ip to the /etc/network/interfaces and restart?

thanks for your help,

João

---

### Post by louieb on 2007-11-06
To the best of my knowledge. If you have 2  network cards the you can have 2 IP addresses.   Haven't see anything  on having 2 IP addresses using a single network card.

---

### Post by poudin on 2007-11-06
looks like it can be done with a single network card by tagging it with

eth0 eth0:1

check this URL out for a sample config.

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by volksman on 2007-11-06
You can configure two IPs to one physical device.  As per the last note eth0 would be one definition eth0:1 would be the second...

---

### Post by mlentink on 2007-11-06
Let's get basic. Do you use a router? In that case, you don't need a separate address for the internet.
Or do you want to use your specific machine as a router?

---

### Post by JoaoCarlosCorreia on 2007-11-08
I have a router and a network.
All windows machines and one ubuntu.
But my point is to have a ip for this network and another to access via router to out of this lan...
Can I do that?

---

### Post by Rafadagaffer on 2007-11-08
Your router will automatically do that for you, all the machines on your lan will take the external ip address of your router when connecting to the internet, there should be no need for extra configuration

---

