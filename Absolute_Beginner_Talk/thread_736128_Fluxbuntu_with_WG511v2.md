---
title: "Fluxbuntu with WG511v2"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by cr0bar on 2008-03-26
Back once more for help.

I have inherited an aging Thinkpad 600E with a P2 366MHz processor, 128MB RAM (upgraded from 64MB) and I stuck in my spare 40GB hard drive. It however lacks a LAN port so the only internet access is via a PCMCIA wireless card or a dialup connection. I tried Xubuntu 7.10 and got the Netgear WG511v2 wireless card working successfully. However it was a bit sluggish (I heard 7.10 is slower than 7.04 on old systems, so might try that next) so I tried Fluxbuntu and I'm very impressed by how smoothly it runs.

Anyway back to my problem.

I got ndiswrapper, ndisgtk and wifi-tools all successfully installed. I followed the instructions for making a config file so whenever I load Fluxbuntu the wireless light comes on. On running wifi-tools via terminal though, it picks up wireless networks but in the terminal window it's showing only irda0 and one other connection, presumably the modem interface but no wlan0.

I'm typing this in Server 2003 (dual-boot), and since I lack a LAN port it's trickier to do things. I got the packages and tars in Windows and copied over to my Fluxbuntu partition and got them installed that way. I know I'm missing one or two important steps here. Any assistance on what it is?

---

### Post by dstew on 2008-03-26
> it's showing only irda0 and one other connection, presumably the modem interface but no wlan0I am confused. Is your wireless working or not? If so, what is your question? The interface name depends on the software, and may be wlan0, eth0, ath0, irda0, or whatever. It has no effect on whether it works or not.

---

### Post by cr0bar on 2008-03-26
Nevermind, got it going. I kinda left out something so obvious it shames me to admit it.

---

