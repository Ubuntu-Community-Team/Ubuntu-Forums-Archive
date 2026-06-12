---
title: "Ubuntu Server Network"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by drndrw on 2008-03-12
Hey guys. I just installed Ubuntu server without a network connection. Now, I want to connect my server to a network, so I can use SSH to administer it from another computer. Currently, it is not showing up on my list of connected devices, so how do I make it so it is connected? Do I have to run a command? Thanks.

---

### Post by SpaceTeddy on 2008-03-12
i think before i will go into editing files i will ask a few questions to further debug your problem.

First off, when you installed the server, did you configure the network then ?if so, how did you configure it ?

also, do you have other computer on your network that have internet access. How is their network configured ? does it happen automaicially ? If there are other computers, please post the output of one of the follow command run on a machines that has internet

for windows:
```
ipconfig /all
```

for linux/ubuntu
```
ifconfig
route -n
cat /etc/resolv.conf
```

as for how to configure your network - this is done in the file /etc/network/interfaces. you will need to edit it directly. to do this i need to know if you have a graphical user interface (i.e. xserver, gnome, kde, anything) or if you are running on a purely CLI (command line interface) based enviroment.

---

### Post by handydan918 on 2008-03-12
Assuming all hardware is recognized, and the ethernet cable is plugged in  :) try ```
sudo dhclient
```

Then you can try to ping the router and/or an external webserver. 
You can also do ```
ifconfig
``` to see if you successfully pulled an IP address.

---

### Post by Iowan on 2008-03-12
I presume you'll eventually want to either give your server a static IP address or set up your DHCP server to issue a static lease.

---

### Post by drndrw on 2008-03-12
Hey guys. I took the lazy way out, and chose to reinstall Ubuntu with a network connection. Works like a charm now! Thanks!

---

