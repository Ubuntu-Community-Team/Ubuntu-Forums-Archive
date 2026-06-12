---
title: "Wireless Troubleshooting Help File"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by robert_rees on 2008-04-06
Ok.  I am running from the LiveCD 8.04 B.

I bought the 2008 Linux Bible, and have been dutifully studying, but I am almost as smart as a moron when it comes to Linux (just to put you in the right perspective.)

I booted up fine and tired to connenct to my wireless.  Like many posts here, I had no luck.  So i went to the troubleshooting FAQ.  This is what I found.  To wrap it up... it does not tell me how to ENABLE the device.  The following text is what I saw.

[B]3.2.2.&#8195;Check for driver  
   1. Open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: sudo lshw -C network
   2. If there is a driver listed then see Section 3.2.3 &#8213; Check device is on.[/B]

ubuntu@ubuntu:~$ sudo lshw -C network
[I]
  *-network:0
description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: XX:XX:XX:XX:XX:XX
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.11 latency=32 link=no mingnt=64 

module=tg3 multicast=yes port=twisted pair
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:xx:xx.x
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:XX:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
ubuntu@ubuntu:~$[/I]

Thanks in advance.  FYI, I changed the MAC addresses to X's for security.

Robert

---

### Post by anewguy on 2008-04-06
I could repeat what's been on several threads, but you seem like you are really trying and wanting to learn.  For Linux, that can mean a lot of hunting through the forums.  So, what you need is to install the Broadcom drivers, either through the restricted manager or via ndiswrapper.  There are MANY, MANY posts on this, so I'm going to let you search the forums for "Broadcom wireless" and see what you find.  I'm not trying to be a bad guy here - in fact you'll find many of my responses to this same problem have included detailed instructions.  I just want you to get used to really searching the forums (the same kind of search at Yahoo! or any other search engine, something like "ubuntu broadcom driver" will get you many hits as well).

Please don't think bad of me - this is the way of Linux and it sounds like you are trying hard!

---

### Post by anewguy on 2008-04-07
To prove I'm not really a bad guy.......follow the information for the wireless in this link.  Don't worry that it's not the same vendor, etc., - everything is the same.

[http://ubuntuforums.org/showthread.php?t=507505]("http://ubuntuforums.org/showthread.php?t=507505")

---

### Post by robert_rees on 2008-04-07
anewguy,
I certainly do not think bad of you for posting a reply.  Thank you for the advice sir.  More often then not (as I used to Admin a help forum) the knowledge comes from knowing what to ask!  To this end, I thank you for guiding me in that direction.

Thanks,

Robert

---

