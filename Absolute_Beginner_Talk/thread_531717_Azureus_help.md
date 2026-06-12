---
title: "Azureus help"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by mbt12 on 2007-08-21
I just installed Azureus, and the three things on the bottom are not green.  Ratio is red, Nat is empty, and DHT Firewalled is yellow.  What do I need to do to fix this?

---

### Post by UltraMathMan on 2007-08-21
I'd recommed checking out the [Azureus Wiki]("http://www.azureuswiki.com/index.php/Main_Page"), especially the First Aid section - lots of great info.

-Hope this helps :)

---

### Post by mbt12 on 2007-08-21
Wish it did, I think I am in way over my head with this.  I have no idea how to fix any of it.

---

### Post by UltraMathMan on 2007-08-21
Ratio - Basically your download to upload ratio. This will become green as you begin to download files and share completed (and partially completed) download.

NAT - Short for Network Address Translation, this need to be green for you to get the best speeds. Basically if you are behind a router on your network, you need to open a port (think of it as a channel for data) on the router to allow Azureus to send data over. Instructions for this depend on the router, see that specific documentation. Once opened see Azureus documentaion (or post back) for info on how to set Azureus to use that port.

DHT - Short for Distributed Hash Table, it is used according to wikipedia, as a distributed tracker to provide rendezvous between clients downloading a particular file. This should resolve itself once a port is opened on the router for Azureus.

---

### Post by mbt12 on 2007-08-21
How do I go about opening ports for ubuntu? I just starting using it and am not real familiar with it.

---

### Post by UltraMathMan on 2007-08-21
You shouldn't have to open any ports in ubuntu - once you open the port on the router and set it in Azureus the firewall in ubuntu should automatically adjust. To check it you can install nmap ```
sudo apt-get install nmap
``` then run ```
nmap 127.0.0.1
``` to display open ports on your machine.

---

### Post by mbt12 on 2007-08-21
Alright I think I am getting closer.  I just need to learn how to set up a static ip.  I have been to the portforwarding web site and they do not have an option for linux.  Any ideas?

---

