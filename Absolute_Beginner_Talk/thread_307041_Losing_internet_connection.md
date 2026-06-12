---
title: "Losing internet connection"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by donang on 2006-11-26
I am baffled by whats going on.  I'm extremely new to Linux though i thought i was getting it figured out (big mistake).  I will give you a brief run down of what i done. I switched from Fedora to Ubuntu because it seemed more user friendly.  I finally got the network fixed where it worked good. No problems with net.  Anyway I thought i had things figured out so i re installed Fedora 6 because the programs i was wanting to use suppose to "work best with Fedora".  Well, once i got it installed i could not get my internet connection to work.  The only way i coould get it to work was unplugging from my ethernet card and plugging back in (i have two NCs...i was using eth0), the only problem was when i closed out firefox i could not connect again until i unplugged from ethernet and plugged back in.  So after finally going crazy, i re installed Ubuntu.  Same problem, i have to unplug cable and plug back in to get it to work, but then i seems to lose connection after trying to get updates.  If i plug in to eth1, it seems to work fine, but i need both NCs.  I tried going in to Firefox and stopping ipv6.  I've activated, deactivated.  I've done everything i know to do.  Was hoping maybe someone knows what i may be missing.  Oh..i cant ping either with ip address or url.      Thanks in advanced

---

### Post by donang on 2006-11-26
bump for help

---

### Post by PotOfVB on 2006-11-26
Firstly how do you connect to the internet?
- Direct connection to internet e.g. single user modem usb/ethernet
- Router/modem e.g single/multi user/s usb/ethernet

Are you using a static IP or DHCP (dynamic IP)?

I connect through a Adsl Modem/Router, I had some problems accessing web pages and using apt-get.

I worked out that my problem was that I had a problem with DNS, the DNS was not resolving the addresses.

I solved this by manually adding the two ISP DNS addresses to:
_/etc/resolv.conf _

It will probably have at least one IP address there already, e.g.

nameserver 192.168.0.1  

find your ISP's DNS addresses and edit _/etc/resolv.conf_

e.g. 
(Don't use the numbers below, each ISP has it's own unique numbers)

nameserver 234.56.789.012
nameserver 234.56.789.013

---

### Post by PotOfVB on 2006-11-27
to edit resolv.conf

1 open terminal:      menu > applications - accessories - terminal

2 in terminal type:   _gksudo gedit /etc/resolv.conf_ 

3 type in your ISP's DNS's: 
  e.g 
[U]nameserver 202.101.23.121
nameserver 202.101.40.232[/U]

4 Save!

hopefully this fixes your problem!

---

### Post by Bachstelze on 2006-11-27
Please use **gksudo** instead of sudo to use graphical apps - like gedit - as root.

---

