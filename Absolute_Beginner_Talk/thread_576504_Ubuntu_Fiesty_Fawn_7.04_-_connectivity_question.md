---
title: "Ubuntu Fiesty Fawn 7.04 - connectivity question"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by FoxFive50 on 2007-10-15
Hi,

I'm a total newbie to Ubuntu (and Linux for that matter). Just installed Ubuntu. I trawled this forum for a answer to my issue already but have not found an answer.

I can browse the internet using Firefox fine. When I use the command line to ping sites i get destination unreachable error. 

I need to run the Update Manager / Software Sources stuff to get latest updates and both these apps fail to connect to security.ubuntu.com - I can connect to this site using Firefox though.

---

### Post by alienexplorers on 2007-10-15
Try entering in terminal:
> sudo apt-get update
and then:
> sudo apt-get upgrade

---

### Post by FoxFive50 on 2007-10-15
update says : Could not connect..... many many times

---

### Post by jw5801 on 2007-10-15
Are you behind a proxy or a firewall?

---

### Post by FoxFive50 on 2007-10-15
> **jw5801 said:**
> Are you behind a proxy or a firewall?

Yes. Any ideas how I can get the details on this? I'm fairly certain my username and password will get me 'through' the firewall - just not sure where to look in XP for the settings ...

---

### Post by jw5801 on 2007-10-15
Go to "System > Preferences > Network Proxy" and set the proxy to whatever it needs to be. Firewall shouldn't be too much trouble after that I don't think.

---

### Post by FoxFive50 on 2007-10-15
> **jw5801 said:**
> Go to "System > Preferences > Network Proxy" and set the proxy to whatever it needs to be. Firewall shouldn't be too much trouble after that I don't think.

copied the settings exactly from my windows pc running firefox onto the ubuntu pc. rebooted ubuntu (is this required?). Internet still works fine. Update manager still fails.

---

### Post by jw5801 on 2007-10-15
Shouldn't require a reboot. You're behind a firewall as well? I'd try switching off the firewall and then running ```
sudo apt-get update
```so we can at least identify if that's the problem.

---

### Post by FoxFive50 on 2007-10-15
I also see the windows machine is picking up a few wireless networks but the ubuntu machine is not.

The Ubuntu machine has a Intel Wireless Lan card. It is a Dell laptop D610.

- Ok will try getting outside the firewall. I'm at a corporate firm so can't just switch off the firewall.

---

### Post by jw5801 on 2007-10-15
Ah, networks you don't have control over always make things more interesting.
As for the wireless, it's fairly likely that there isn't a driver installed for the card as yet. The command ```
lspci
```should tell you specifically what chipset you have and if you put that into the forum's search function it's fairly likely you'll return a how-to for the card. The line you're looking for will read something like this:
[quote=lspci]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
**05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)**
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)[/quote]
Although the bit after Network Controller will probably be different. I've just posted mine as reference.

---

### Post by FoxFive50 on 2007-10-16
Went to an internet cafe last night and it worked fine. Thanks for all the help. It must have been the firewall.

---

