---
title: "ICS in Linux"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by brander on 2007-03-13
Hi, I`m looking for the Linux equivalent of Windows Internet Connection Sharing. Currently, a Windows PC has two net cards, net1 connects to the cable modem and net2 connects to a switch. Any computer plugged in to the switch gets an ip via DHCP and has full internet ability.

I have set up a Linux box with two net cards, eth0 and eth1, to replace this but can`t find any setting for sharing the Internet Connection. Is there something simple to do or will it just work automatically?

---

### Post by Bachstelze on 2007-03-13
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

---

### Post by Xappe on 2007-03-13
I guess that firestarter, as a frontend to iptables, can setup your internet connection sharing in a graphical manner :)

You can find and install firestarter in the repositories using the Synaptic package manager or plain apt-get.

---

### Post by brander on 2007-03-13
Ugg, so complicated. In Windows, the DNS and Gateway are all set to 192.168.0.1 automatically by just selecting Share this Connection on one of the connections. IPs are then handed out to anything which connects via DHCP. 

Until it is that simple in Linux I think I`ll keep my Windows server, but thanks for the information.

---

### Post by bravemosquito on 2007-03-15
[http://www.pfsense.com/](http://www.pfsense.com/)

[http://m0n0.ch/wall/](http://m0n0.ch/wall/)

[http://www.freesco.org/](http://www.freesco.org/)

[http://www.coyotelinux.com/](http://www.coyotelinux.com/)

Which wanna choose? :)

---

### Post by lamalex on 2007-03-15
> **brander said:**
> Ugg, so complicated. In Windows, the DNS and Gateway are all set to 192.168.0.1 automatically by just selecting Share this Connection on one of the connections. IPs are then handed out to anything which connects via DHCP. 

Until it is that simple in Linux I think I`ll keep my Windows server, but thanks for the information.

it's actually very simple and much more secure to have a linux box routing than a windows box routing. probably (as in definitely) worth your time to set up.

---

### Post by Robynsveil on 2007-04-05
> **Iamalex said:**
> it's actually very simple and much more secure to have a linux box routing than a windows box routing. probably (as in definitely) worth your time to set up.
I tend to agree with Brander that the Linux box *is* more complicated to set up... but that's only *if* you have decided you want Linux to behave like Windows, which defeats the whole purpose of using Linux in the first place. *If* you're content with setting up a system fraught with vulnerabilities and foibles *just* because you can do it all via a GUI and wizards, then use Windows. Otherwise, if you want a system that will give you trouble-free performance - one that you can just leave on for months on end and never have to worry about installing security patches or cleaning up clutter or worrying that it might simply reboot for no apparent reason - then choose a Linux distro... but be prepared to work a bit, learn a bit and ultimately have the satisfaction that you've been able to really *accomplish* something (thanks to this fine forum and the generous, patient gurus that are ever ready to help).
If you're having second thoughts about Linux in the first place, this article should help you make up your mind:
[http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm"):)

---

