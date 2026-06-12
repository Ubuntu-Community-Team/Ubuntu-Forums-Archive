---
title: "Modem driver"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Showan on 2006-01-20
Hi

first of all I want to say that Ubuntu looks and feels great!

Unfortunately I am a complete Linux noob, so it took me a while just understand the basics (especially about the root user)

All hardware is detected and installed properly, except for my ADSL modem (alcatel Speed touch PC PCI)
So i went googling and found out that it needs Itex 1483 drivers
But the latest drivers are for 2.4.16 kernel, Itex wet bankrupt

Is there no solution for my problem except for downgrading or buy a new modem?

PS: In windows, I have 2364 drivers, but  that makes no difference or am I wrong

thanks in advance

---

### Post by L Campbell on 2006-01-20
[QUOTE=Showan]Hi

first of all I want to say that Ubuntu looks and feels great!

Unfortunately I am a complete Linux noob, so it took me a while just understand the basics (especially about the root user)

All hardware is detected and installed properly, except for my ADSL modem (alcatel Speed touch PC PCI)
So i went googling and found out that it needs Itex 1483 drivers
But the latest drivers are for 2.4.16 kernel, Itex wet bankrupt

Is there no solution for my problem except for downgrading or buy a new modem?

PS: In windows, I have 2364 drivers, but  that makes no difference or am I wrong

thanks in advance[/QUOTE]


You might want to take a look at   [http://linmodems.org/](http://linmodems.org/)

They're kind of a center of knowledge for Linux modems.

---

### Post by banane33 on 2006-01-20
Hi!

I have the same problem with a Itex ADSL PCI modem.

The suggested link, linmodems, is about regular modems, not DSL modems.

I have found that my modem and probably Showman's modem are based on the Itex Apollo Chipset. There is a page suggesting drivers ([http://dsl.linux.it/ChipsetItex]("http://dsl.linux.it/ChipsetItex")), but these drivers are for the 2.4 kernel, and Ubuntu Linux 5.10 is Kernel 2.6. 

I am new to Linux, is it possible to run 2.4 drivers on a 2.6 kernel? Would it be hard for someone to convert the 2.4 drivers to 2.6? Is there any solution?

Thanks!

Other sites with information about this modem chipset :
[http://www.modem-help.com/chipsets.php?mid=133&nbd=10642]("http://www.modem-help.com/chipsets.php?mid=133&nbd=10642")
[http://www.massey.ac.nz/~mgwalker/misc/adsl/]("http://www.massey.ac.nz/~mgwalker/misc/adsl/")

---

### Post by Showan on 2006-01-21
hi

Fortunately second hand DSL modems are cheap here.

Will a USB modem work, or does it depend on the model?

thanks

---

### Post by Showan on 2006-01-21
Hi

I searched around and found out that ethernet modems are much easier to install under Linux

Since I have a small LAN network, my eye dropped on the TOPCOM Webr@cer 881

It claims to be a ADSL modem/router/switch/access point and this all for a very reasonable price: [http://tools.topcom.net/userguides/Webr@cer%20881%20PSTN%20-%20E-NL-FR-D-SW-DK-NO-FI-SP-PT.pdf](http://tools.topcom.net/userguides/Webr@cer%20881%20PSTN%20-%20E-NL-FR-D-SW-DK-NO-FI-SP-PT.pdf)
This is just what I need!

But will it work under this and future versions of Ubuntu?
What about firmware? Any experiences?

My sisters computer is now connected to mine with a Crossed UTP cable... I guess I have to change to straight to connect to the modem?

Many thanks in advance!!

---

