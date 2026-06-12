---
title: "Installed Ubuntu 18.04 LTS on a MacBook Air 1,1 (early 2008)"
date: 2018-09-27
forum: Apple Hardware Users
---

### Post by tmwong on 2018-09-27
Hi all:

I more-or-less successfully installed Ubuntu (well, Lubuntu) 18.04 LTS on a MacBook Air 1,1 (early 2008). It took about a day of crawling through various online forums to get everything to work, and I wanted to summarize my experience here to save anyone else working with an old Mac a lot of hassle. The main issues that I had were:


[LIST=1]
[*]Broadcom WiFi card: The MacBook Air 1,1 comes with a built-in Broadcom 4321-based WiFI card. The firmware for the card is proprietary, so you will need to install after initial setup. Assuming that you have a USB wired Ethernet adapter available and connected, open up a command line terminal and run [FONT=courier new]sudo apt-get install firmware-b43-installer[/FONT] to download the firmware. [FONT=courier new]apt-get[/FONT] will also install [FONT=courier new]b43-fwcutter[/FONT] to extract and install the firmware. Do *not* install the proprietary Broadcom driver package [FONT=courier new]bcmwl-kernel-source[/FONT], as it blacklists the standard [FONT=courier new]b43 [/FONT]kernel module.
[*]WiFi networks not available: Even after installing the Broadcom firmware, I found that after a reboot my MacBook would not scan for WiFi SSIDs. My current solution is to suspend and resume Ubuntu, which appears to kick the WiFi driver stack awake; I am at a loss to understand why this should help, but...
[*]Slow boot: Booting (and resuming after suspend) are painfully slow out of the box. The solution is to edit [FONT=courier new]/etc/default/grub[/FONT] and add [FONT=courier new]video=SVIDEO-1:d[/FONT] to [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT[/FONT]:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=SVIDEO-1:d"
```
This works around some issues in the drivers for the Intel integrated video chipset.
[/LIST]

If you are trying to resurrect some old Macs these tips might help you. Good luck!

---

### Post by oldfred on 2018-09-27
Moved to Apple sub-forum.

---

### Post by bennywas on 2018-09-30
This is great, thanks!
I've fixed a lot and am now working on the issue of slow internet. Did you happen to find any solutions for this?

Ubuntu 18.04 partition's speed: Ping 24ms, Download 2.90Mbps, Upload 0.96Mbps
macOS partition's speed: Ping 30ms, Download 48.90Mbps, Upload 11.64Mbps

---

