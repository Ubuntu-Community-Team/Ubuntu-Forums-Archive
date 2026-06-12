---
title: "Problems With Network Card not being recognised by Ubuntu Feisty"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by brentos2004 on 2007-12-13
Hi,

Im relatively new to Ubuntu and need some advice. I recently installed Ubuntu Server 7.04 on a testing machine we use at work to act as an FTP server for a new backup solution. Everything was working fine but I needed to add more disk space. Anyway to cut a long story short ive removed the hard disk with ubuntu on into a new machine that has another 2 360gb disks in. Problem is the new machine is a different make (Dell 8300) and its not recognising the onboard or pci network adaptors that are installed. When I run lspci it shows the two network cards in the list without any errors/suggestions so im assuming its a driver problem. Is there anyway I can force ubuntu to load the drivers for the new network cards? or delete the old network settings so that it recognises the new cards? I need to get this working a.s.a.p so any help or suggestions would be appreciated.

Thanks
Brent

I should also add that when I do an ifconfig the only thing that shows up is the loopback configuration. The original setup had static ip settings and was forced to 100mb full duplex at boot up using /etc/networking/interfaces file which is still there.

---

### Post by quinnten83 on 2007-12-13
I don't know much about the network card.
It alsmost sounds to me like the network card is working, but the connection might not be properly configured.
If drastic enough, you might consider moving the data to a seperate home partition and reinstalling.

---

### Post by brentos2004 on 2007-12-13
It is strange, its as if it knows the network cards are there but cant load them due to having the wrong drivers loaded. Im not sure though!. if I try and bring the interface up ifconfig eth0 up it just says "Error while getting interface flags" When I boot from the cd and put it in recovery mode it recognises both network cards and allows me to configure them but as soon as I reboot and run ifconfig theres nothing there!

Help!!!!

---

### Post by brentos2004 on 2007-12-13
Any Ideas people? Im really struggling with this :confused:

---

### Post by OhioYJ on 2007-12-13
I'm by now means an expert, but why not just do a fresh install?

---

### Post by brentos2004 on 2007-12-13
Wellthis is what I will do if there is no way around it. :confused:

---

