---
title: "Wired LAN only works when plugged in a boot"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-05-24
I have a slight issue with my laptop and Ubunutu.  The wired ethernet connection only works when the cable is plugged in when I boot/restart the machine.  If I start up the machine without the cable plugged in, it won't work.  Unfortunately, I am at work right now and don't have my laptop with me, so I can't pull any info about the device.

I do have a Toshiba Satellite series, I purchased it about a month ago.  

Thanks.

---

### Post by aroch1 on 2007-05-24
I have this problem, and im not exactly sure what the culprit is...here's the remedy I use:

```
sudo ifdown eth0
sudo ifup eth0
```

That usually does it for me

---

### Post by Sparkster185 on 2007-05-24
Thanks for the suggestion, I will try this when I get home.

Since I'm not the only person with this problem, do you more experience Ubuntu users think I should file a bug report in Launchpad?

---

### Post by dannyboy79 on 2007-05-24
it's related to hotplug or udev I beleive. basically when you plug something in, a daemon sees it and is suppose to know what to do with it. in your case it appears as though the daemon isn't seeing that you plugged in a ethernet cord. what does 

dmesg | tail
output if you enter that in a terminal immediately following plugging in the ethernet plug?

also can you please show me the output of

lspci -v
this should output the chipsets of your motherboard and all your pci devices.

---

### Post by Sparkster185 on 2007-05-24
dmesg | tail :

```

ACPI: Power Button (CM) [PWRB]
ACPI: AC Adapter (on-line)
ACPI: Battery Slot [BAT1] (battery present)
ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
ADDRCONF(NETDEV_UP): eth1: link is not ready
usb 2-1: new low speed USB device using uhci_hcd and address3
......

```

I believe the relevant line here is ADDRCONF(....


lspci -v :
(this is not the entire thing, as it's long and I'm on my desktop right now due to WiFi issues)
```

05:00.0 Ethernet controller: Realtek Semiconductor Co./ Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
Subsystem: Toshiba America Info Systems Unknown Device ff00
Flags: bus master, fast devsel, latency 0, IRQ 18
I/O ports at 4000 [size=256]
Memory at da000000 (64-bit, non-prefetchable) [size=4k]
[virtual] Expansion ROM at d4000000 [disabled] [size=64k]
Capabilities: <access denied>

```

---

### Post by Sparkster185 on 2007-05-24
> 
sudo ifdown eth0
sudo ifup eth0


I tried this and it did not work.

Output of sudo ifdown eht0
```

RTNETLINK answers: no such process
There is already a pid file /var/run/dhcclient.eth0.pid with pid 8062
killed old client process, removed PID file
Internet Systems Consortium DHCP client V3.0.4
Copyright ....
.....
Listening on LPF/eth0/00:16:.........
Sending on LPF/eth0/00:16.....
Sending on Socket/fallback
DHCPRELEASE on eth0 192.168.0.1 port 67

```

Output of sudo ifup eth0
```

There is already a pid file /var/run/dhcclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP client V3.0.4
Copyright ....
.....
Listening on LPF/eth0/00:16:.........
Sending on LPF/eth0/00:16.....
Sending on Socket/fallback
DHCPDISCOVER  on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER  on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER  on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER  on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping

```



UPDATE:  I just did a suspend, wake-up with the cable plugged in and it was recognized.  This isn't terribly bad anymore, since I don't have to reboot, but I'd still like to figure it out.

---

### Post by lambfrier on 2007-07-30
The solution is to reload the network module.  Try:

```

sudo ethtool eth0
sudo ifdown eth0
sudo rmmod r8169
sudo modprobe r8169
sudo ethtool eth0

```

The 'Link Detected' line should change from 'No' to 'Yes'

You can put this in a script to run whenever you plug an ethernet cable in.

It looks like this is fixed in Gutsy:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798)

---

