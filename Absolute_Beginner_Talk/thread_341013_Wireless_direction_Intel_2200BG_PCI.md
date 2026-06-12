---
title: "Wireless direction: Intel 2200BG PCI"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Spr0k3t on 2007-01-18
I need some help configuring the wireless card on my laptop.  I've got limited access to the internet with my laptop until I can get the wireless card configured correctly.  Please remember that I'm a Linux newb but willing to learn.  Let me give the lowdown of my progress thus far.

**Hardware**
The laptop is an Alienware m5500 Area-51 and it has the Intel 2200BG PCI card.  The router is a DLink DIR-635 and it's been configured with WPA2-PSK (read on, it's changed).  I've successfully configured the laptop as a dual boot system to help my wife make the jump to Linux.  The router is a Draft-N router with minimal support for WEP.  It's there, but the net speed drops when I use WEP instead of WPA or WPA2.  The laptop has a physical switch on it to enable the wireless card and I've verified the connectivity in that other operating system.

**Router Changes**
I changed the router to use no encryption and turned off mac filtering for testing purposes.

**Steps Taken**
With a stock install of Ubuntu Edgy I ran the updates/upgrades wire connected and configured DHCP.  Doing iwconfig in a terminal, my wireless card shows up as eth1.  I tried to configure the connection direct to the router by the command:  "sudo iwconfig eth1 essid <idName> channel <num.>".  The odd part is, I'm not prompted for my su pass, I just get a newline prompt as if I hit return.

I did a "sudo iwlist eth1 scan" and found about 15 access points successfully (external antennas are wonderful).  I'm either missing the last step I need to do or I've missed a step in the process of trivial configurations.

**Plans**
When I get a successful configuration going, I'm going to get at least WPA working if I can.  I'm not sure if WPA2 is an option, but the hardware does support the option.  I wonder if there might be a driver which supports WPA2 encryption.

Considering this is Linux day #2 and having only spent a total of four hours solid researching and testing, I feel as if I'm doing pretty good.

---

### Post by riven0 on 2007-01-18
So you're almost there. But network manager may be what you need to get up and running completely. So try that first and see what results you get:

> sudo apt-get install network-manager

If that doesn't work, connection manager may suit you better.

---

### Post by Spr0k3t on 2007-01-18
Thanks I'll give that a shot and report my findings.

---

### Post by Spr0k3t on 2007-01-18
I'm sorry to say, but this didn't work.  I installed the network-manager and it will not see any wireless connections regardless of what I do.  I can still scan without any problems and see my wireless network and several other access points.  I did a search for the "connection manager" but came up empty handed.

Thanks again for the help, but I'm still stumped.

---

### Post by Spr0k3t on 2007-01-19
I got it.  I did some checking to make sure I had the latest updates and after installing these updates and rebooting, it worked.  I also installed better drivers for my graphics card while I was at it.  The CM works good, but I can't figure out how to keep wired and wireless connected at the same time.

A note for other new users interested in this information, make sure that you disable the wireless card from the Networking dialog to get the wireless working as well.  I read that in another thread and verified this to be true.

---

