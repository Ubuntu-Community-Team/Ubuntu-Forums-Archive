---
title: "Server ip change?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-11-21
is there anyway that i can setup a static ip for my server like a custom one because the one that i am using right now is shared so is there anyweay that i can set one up or change the current static ip

---

### Post by cmnorton on 2007-11-21
I am assuming you are sharing this IP address only when the other system is not running or its network cable is unplugged.

You should be able to go into Networking and change your IP address, but you've got another problem. Anything that depends on that address, daemons in /etc/init.d, config files, and so on are going to have to be changed as well.

---

### Post by fedex1993 on 2007-11-21
ouch that not going to be good to mess with hmmm ahh guess will leave the current ip on it and just switch it on my desktop. ty cmnorton

---

### Post by OffAxis on 2007-11-21
you should be able to set up a static IP assignment at your router based on your server's MAC address.

---

### Post by cmnorton on 2007-11-21
I've had to do it a lot. It's not pleasant. It might be faster to change the system with which you are sharing to another IP address or even DHCP, if the other system is not a server. To change IP references, you'd need to know what's installed on this server and where the config files are. You'd wind up making some changes, having some things not work, tracking down what those are, fixing those references, restarting the system, and fixing some more things.

---

