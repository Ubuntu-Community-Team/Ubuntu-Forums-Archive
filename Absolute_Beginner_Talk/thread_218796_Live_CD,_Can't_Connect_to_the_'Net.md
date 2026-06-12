---
title: "Live CD, Can't Connect to the 'Net"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Anthraxx on 2006-07-19
I'm using the Live CD and trying to connect to the 'net. My router is a D-Link DSL 504T. The connection type is PPPoE. When I put pppoeconf into the terminal, it recognises my onboard NIC, scans it, but then it says the access concentrator of my provider didn't respond. Can anyone help me to connect to the 'net?

Thanks.

---

### Post by Derek Djons on 2006-07-19
Correct me if I'm wrong but routers have to be configured. In your case it has to be filled with PPPoE and provider data.

When installing a new OS you don't have to change anything. If your router is set on DHCP your OS will receive automatically an IP address. If you're working static you just have to enter the IP, Sub, Gateway and DNS.

---

### Post by Anthraxx on 2006-07-19
I've configured the router and it workes fine with XP, it's what I'm connected with now. Under Ubuntu I tried it on DHCP, and I also tried setting the DNS, Subnet Mask and Default Gateway the same as XP, and the IP to the same except the last variable. I reconfigged the router to accept the new IP, too.

I should probably say that putting my router's IP into Firefox in Ubuntu works, alowing me to change the settings and stuff, I just can't connect under Ubuntu. My mum's computer's net connection is unaffected by this, if thats of importance (its on the same router).

Thanks. I'll give it a try after posting this, but assume it failed unless I post back :).

---

### Post by Anthraxx on 2006-07-22
[QUOTE=Terminal]0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I /O Controller (rev 04)

0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Roo t Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High De finition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface  Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family ) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Contr oller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PC IE)] Secondary
0000:06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 V E (LOM) Ethernet Controller (rev 01)
[/QUOTE]
This is what I get when I type lspci into the Terminal.

---

### Post by alexus_fs on 2006-07-22
See:
[http://www.ubuntuforums.org/showpost.php?p=1286987&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1286987&postcount=1)
for the solution.

---

