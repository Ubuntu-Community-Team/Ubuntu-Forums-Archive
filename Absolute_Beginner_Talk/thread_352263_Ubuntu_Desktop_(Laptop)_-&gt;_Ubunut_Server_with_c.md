---
title: "Ubuntu Desktop (Laptop) -&gt; Ubunut Server with crossover ethernet cable."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by brooky on 2007-02-03
Hello,

I have a PC setup as a server running slimserver on Ubuntu server edition. I also have a laptop with desktop edition on. 

I want to connect to the Ubuntu server with an ethernet crossover cable. However the laptop can't seem to find the server at all (called home).

The server has OpenSSH installed on it to and I can't connect to it either with a crossover cable. 

The annoying thing is that when the sever was on the LAN in the office it all worked fine!?

How can I connect with a crossover cable to SSH?

home:22 using putty doesn't work. [http://home:9000](http://home:9000) for slimserver doesn't work. :(

Any advice much appreciated.

---

### Post by danielph on 2007-02-03
Can you ping the server?

---

### Post by Quintin Riis on 2007-02-03
First rule of troubleshooting is always:

CHECK THE CABLES.

Confirm that you're using a known good crossover cable.

Past that, depending on how you have resolution setup the machines might not be able to communicate via hostname.

To connect 2 machines over a crossover cable, you just need to give each a static IP address on the same subnet.

Set one to, for example, 192.168.1.5,netmask 255.255.255.0, and the other to 192.168.1.6, netmask 255.255.255.0.  Gateway, of course, is blank since no routing is going on; the computers are communicating directly on the same network.

---

