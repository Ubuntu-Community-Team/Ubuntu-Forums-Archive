---
title: "Ubuntu---&gt;Windows"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by AlexBIOSS on 2007-12-12
Hello,
I want to get started with Ubuntu (linux in the process) on my desktop and I need to connect it to the internet. The internet is being used by a computer running windows. I have a ethernet LAN cable running between the 2 computers and the internet connection on windows I have set the properties to share. On Ubuntu I searched the network places and saw a windows icon appear, but it did nothing when clicked on and Ubuntu does not have its internet working. The connection on the windows machine is through usb and I do not have a wireless router. I do not know what is meant by a switch either.
From another post I gathered this suggestion, but should this work?

Code:
sudo gedit /etc/network/interfaces
and add the following lines:
Code:
auto eth0
iface eth0 inet static
address <your ip>
subnet <your subnet>
gateway <your windows machines ethernet cards ip address>
and then restart networking:
Code:
sudo /etc/init.d/networking restart

How should I go about the problem?
Thanks, Alex M.

---

### Post by shadow-of-sin on 2007-12-12
That suggestion you posted should work. What happens when you try that?

Oh and remember to back up before editing:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

---

### Post by markyb86 on 2007-12-12
A standard ethernet cable will not work, even if configured correctly. You need a [crossover cable.]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

Oh and a switch is just like a hub, only it allows full bandwidth to all of its ports, and controls the packet flow better.

---

### Post by louieb on 2007-12-12
Sometimes a regular Ethernet cable will work depends on your network cards. If it doesn't the you probably need to get  whats called a crossover cable. It a cable thats is wired  to simulate  both computers being plugged into a hub or router.

---

