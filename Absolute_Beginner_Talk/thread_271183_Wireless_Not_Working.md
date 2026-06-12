---
title: "Wireless Not Working"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Thenotsowyzewun on 2006-10-04
Hi,

I can see my Wireless card in Network Manager (Sys > Admin > Networking) and I've set it to DHCP and made it the default gateway, and it's recognized the SSID of the network but it's not connecting to it -


I tried PING [www.micro.com](www.micro.com) and it says unknown host (& Firefox isn't working either, obv)

Here's the (relevant) output from iwconfig (retyped by hand!):

```
wlan0

IEEE 802.11b+/g+ ESSID:"marcus_brook" Nickname "acx v0.3.21" Mode: Managed Frequency: 2.412Ghz Access Point: Not-Associated Bit Rate: 54 Mb/s Tx-Power=15 dBm Sensitivity=1/3
Retry min limit: 7 RTS thr: off
Power Management: Off
Link Quality: 39/100 Signal Level: 15/100 Noise Level: 0/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

Not sure where to go from here, I tried to connect to an AP using:

```
sudo iwconfig wlan0 marcus_brook ap 192.168.0.1 mode managed commit
```

but it just said:

Error: Unrecognized wireless request "marcus_brook"

Can anyone help?

---

### Post by bensexson on 2006-10-04
Is your AP using security and if so what kind?

---

### Post by Thenotsowyzewun on 2006-10-04
No WAP nor WEP nor security of any kind. Never got around to it.

---

### Post by bensexson on 2006-10-04
try sudo wlan0 essid marcus_brook enc off

---

### Post by Thenotsowyzewun on 2006-10-04
wlan0: command not found

So I tried sudo iwconfig wlan0 essid marcus_brook enc off

No output, but no complaints neither, so I tried ping [www.micro.com](www.micro.com), to no avail :(

Then I re-opened Network Manager to see if anything had changed, nada :(

EDIT: Just tried

sudo iwconfig wlan0 essid marcus_brook enc off commit

just in case commit needs to be there. Nothing happened though.

---

### Post by Crooksey on 2006-10-04
sudo /etc/init.d/networking restart

It might just be network, im not sure.

---

### Post by Thenotsowyzewun on 2006-10-04
No you were right, it's networking :).

It flew through the wlan0 and eth0 (the first bit), couldnt find DHCP for eth0 ('cos it's not plugged in!) and then did DHCPDISCOVER for wlan0 too and couldn't find nothing:

No DHCPOFFERS received.

And I just realized, I think I manually typed marcus_brook (the ESSID) into Network manager, a week or two again when I first tried to get this working, so I just checked and yep if I manually delete the writing, and disable and active the interface it doesn't detect it again, that drop-down just remains blank (and it took ages to activate too, not sure whether it actually succeeded).

BTW, whilst I'm waiting for the forum to complete their update:

<CODE>sudo lshw -C network</CODE>

*-network
description: Wireless Interface
product: ACX 111 54Mbs Wireless Interface
vendor: Texas Instruments
physical id: 5
bus info: pci@04:05.0
logical name: wlan0
version: 00
serial: ******** (the mac)
width: 32bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
resources: iomemory:ff5fe000-ff5fffff iomemory:ff5c0000-ff5dffff irq:217

Not sure if that'll help.

---

### Post by Thenotsowyzewun on 2006-10-04
Cool the sites back up. Anyway:

No you were right, it's networking :).

It flew through the wlan0 and eth0 (the first bit), couldnt find DHCP for eth0 ('cos it's not plugged in!) and then did DHCPDISCOVER for wlan0 too and couldn't find nothing:

No DHCPOFFERS received.

And I just realized, I think I manually typed marcus_brook (the ESSID) into Network manager, a week or two again when I first tried to get this working, so I just checked and yep if I manually delete the writing, and disable and active the interface it doesn't detect it again, that drop-down just remains blank (and it took ages to activate too, not sure whether it actually succeeded).

BTW, whilst I'm waiting for the forum to complete their update:

<CODE>sudo lshw -C network</CODE>

*-network
description: Wireless Interface
product: ACX 111 54Mbs Wireless Interface
vendor: Texas Instruments
physical id: 5
bus info: pci@04:05.0
logical name: wlan0
version: 00
serial: ******** (the mac)
width: 32bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
resources: iomemory:ff5fe000-ff5fffff iomemory:ff5c0000-ff5dffff irq:217

Not sure if that'll help.

---

### Post by dragonfyre13 on 2006-10-04
OK, lets lay down a bit of info first.

1. Wlan card type
2. running Ubuntu, Kubuntu, Xubuntu, etc?
3. You mentioned before that there was no security. That's good.
4. What kind of router?
5. output of dmesg

Also, a few things to try. If you aren't adverse to installing a few KDE Libs, try kwifimanager to configure the wifi network. That's how I got mine to work.

What happens if you ping the router? (Don't try to ping an outside site. It adds about 50 more variables into the equasion that could screw things up)

---

### Post by Thenotsowyzewun on 2006-10-04
Wlan card type? If you mean make and model, it's a Safecom somethingorother... (if this is what you mean I'll find out).

Running Ubuntu.

Yep, no security, I'll leave that for now.

Router: Netgear router plugged into ADSL, with a separate Netgear Wireless adapter (802.11a/b compatible).

Sorry, I can't get you the output of dmesg, the computers not booting up now. I'll repost with full info once I've sorted out the MBR and NTLDR and GRUB... (got another post about that).

---

