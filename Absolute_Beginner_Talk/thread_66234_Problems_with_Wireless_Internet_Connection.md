---
title: "Problems with Wireless Internet Connection"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by AndieB on 2005-09-16
Hi all!

I'm a total newbie to Ubuntu and to Linux aswell.

I have installed Ubuntu version 5.04 from a CD-ROM on a Laptop (IBM).
I use a D-Link DWL650 pc-card adapter. I also have a Netgear Wireless ADSL Router.

My problem is this, it takes awefully long time for the computer to connect to
internet. When surfing the web with Firefox, I have turned off the IPv6 (with about:config) in Firefox. But that hasn't solved my problem.

Becuase I have the same "slow" problem if I run a IRC client or try to update my
system with the Synaptic Package Manager.

It get the sense that it takes time for my laptop (Ubuntu) to do the DNS
communication or something like that.

I also have a Windows XP box with a Wireless adapter and that works just fine,
goes fast as it can do.

What is my problem?
Anyone who can give me helpful tips?

Please write in "step-by-step" or something, since I'm so newbie to Linux and Ubuntu.


Thankful for anykind of help!

Best regards,

Andreas

---

### Post by davmac on 2005-09-16
Andreas,

Could be the incorrect setting of the DNS. If you type in "sudo cat /etc/resolv.conf" without the quotes what do you get? The IP addresses that it shows, are these what you'd expect to see for the DNS addresses for your ISP?

Dave Mac

---

### Post by AndieB on 2005-09-16
Hi Dave, 


I haven't checked that what you wrote, becuase I'm not at the place where
I have my laptop. I forgot to give you some configuration details:

The Laptop has STATIC IP: 192.168.2.3
The Router (Wireless) IP: 192.168.2.1

It is set to use the Router to resolve DNS becuase the Router is using
DHCP from the ADSL ISP. The Router should "forward" the DNS queries if
it can not resolve it itself.

Should I still check the config file as you wrote?

Thanks for your time and effort!

Best regards,
 Andreas

---

