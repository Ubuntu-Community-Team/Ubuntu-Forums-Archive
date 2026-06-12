---
title: "Wifi connect on dual-boot laptop fails in Ubuntu, but not Mac OS X"
date: 2016-06-30
forum: Apple Hardware Users
---

### Post by Peter_R._Wood on 2016-06-30
I'm running Ubuntu Desktop 16.04 on a MacBook 13" (on which I also dual-boot Mac OS X 10.7.5). This laptop has a Broadcom wireless card: "Broadcom BCM4328 802.11 Wireless Controller" according to Mac OS X. In Ubuntu, I'm using the proprietary Broadcom STA Wireless Driver. I connect the laptop wirelessly to a TP-Link WDR-3600 wifi router, which is running OpenWRT 15.05.1. It has two Atheros wifi chips built in, one for the 2.4GHz band and one for the 5GHz band. I have a separate SSID for each band, but both are set up with the same authentication credentials. In OpenWRT, the hardware for the 2.4GHz band is listed as "Generic MAC80211 802.11bgn" and the 5GHz band is listed as "Atheros AR9580 802.11an".

The problem I'm experiencing right now is that, when I choose to connect to the 2.4GHz band SSID using Ubuntu, my passphrase is accepted, and the connection seems to negotiate for a minute or so, and then either shows as disconnected, or shows as connected but has no IP connectivity. Either way, there is no actual IP connectivity when I try to ping other hosts or browse the web. If I then attempt to connect to the 5GHz band SSID, the connection is successful almost immediately, and ping/web browsing/etc works normally. The problem with connecting to the 2.4GHz band persists across deleting/recreating the wireless connections in the network manager, as well as across reboots.

When I reboot the computer into Mac OS X and try to connect to the 2.4GHz network, it works immediately, as does the 5GHz network.

No other Mac or Linux computers, or iDevices, in the household are having this same issue.

I'm trying to determine whether the problem lies in the computer hardware, operating system, router hardware, or router operating system, or if it's some unique combination of all four factors that causes the issue. Right now, my best guess is that Ubuntu's DHCP client isn't getting along well with OpenWRT's DHCP server, but I'm not sure why or who's to blame, or what to do further to diagnose the issue.

If anyone has suggestions on how to proceed, please let me know. I've included relevant log file data as Gists on Github. I plan to cross-post this in the OpenWRT forums.

Connecting from Ubuntu:
Syslog from Ubuntu when trying+failing to connect to the 2.4GHz band: [ubuntu_syslog_2.4GHz.txt]("https://gist.github.com/prwood/7dd822e5323fe1fad7d578609c0f586a")
Syslog from Ubuntu when connecting to the 5GHz band: [ubuntu_syslog_5GHz.txt]("https://gist.github.com/prwood/5d218c32033ed45fb58c154d4be9a9dc")
Syslog from OpenWRT when trying+failing to connect to the 2.4GHz band: [openwrt_syslog_2.4GHz.txt]("https://gist.github.com/prwood/4ea38f6d782f1ace7db65024a3b1bc03")
Syslog from OpenWRT when connecting to the 5GHz band: [openwrt_syslog_5GHz.txt]("https://gist.github.com/prwood/00b0fb7a991004f177d5dbfb43e29c61")

Connecting from Mac OS X:
Syslog from Mac OS X when connecting to the 2.4GHz band: [mac_syslog_2.4GHz.txt]("https://gist.github.com/prwood/40c2d877dc5e6c40bc03849776688b73")
Syslog from Mac OS X when connecting to the 5GHz band: [mac_syslog_5GHz.txt]("https://gist.github.com/prwood/08f0cd4105381f6e5b3b8618ee1d334c")
Syslog from OpenWRT when connecting to the 2.4GHz band: [openwrt_mac_2.4GHz.txt]("https://gist.github.com/prwood/c550044c4791c8db86c775c6f98d8ffc")
Syslog from OpenWRT when connecting to the 5GHz band: [openwrt_mac_5GHz.txt]("https://gist.github.com/prwood/af3b52dce6b2d22fe2bb8803895b42b0")

---

### Post by &amp;KyT$0P# on 2016-06-30
It looks like Ubuntu is not receiving the DHCPv4 reply in the 2.4 GHz log, even though your router is sending it.  Have you customised firewall on Ubuntu?

---

### Post by Peter_R._Wood on 2016-07-01
> **halogen2 said:**
> It looks like Ubuntu is not receiving the DHCPv4 reply in the 2.4 GHz log, even though your router is sending it.  Have you customised firewall on Ubuntu?

Nope, no firewall running in Ubuntu at the moment.

A few other interesting developments:

I did some further diagnosis using tcpdump, and it looks like my laptop running Ubuntu *can* hear the DHCP response from the router, but seems to be ignoring it... at least when connecting over the 2.4GHz band. This tcpdump is filtered on ethernet traffic going to or from my laptop's wireless hardware address.

```

# Laptop makes its first DHCP request:
06:15:14.023136 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300

# A couple of seconds later, the router pings my localhost (which apparently already has an IP - maybe it's remembered from a previous connection on the 5GHz band?):
06:15:16.289048 IP 192.168.1.1 > 192.168.1.123: ICMP echo request, id 31123, seq 0, length 28

# The router replies to the laptop:
06:15:16.292735 IP 192.168.1.1.bootps > 192.168.1.123.bootpc: BOOTP/DHCP, Reply, length 300

# Laptop just keeps requesting DHCP:
06:15:16.292980 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300
06:15:19.081031 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300
06:15:26.254678 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300
06:15:35.206999 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300
06:15:38.944939 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300
06:15:43.250495 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300
06:15:48.030354 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300
06:15:56.863511 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300

```

At that point, the laptop gives up.

When connecting to the 5GHz band, however, it's much simpler:

```

# Laptop makes its first DHCP request
06:16:29.291264 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300

# Router responds to DHCP request
06:16:29.295006 IP OpenWrt.lan.bootps > 192.168.1.123.bootpc: BOOTP/DHCP, Reply, length 300

# Laptop makes a second DHCP request
06:16:29.295294 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:23:12:04:c4:a9 (oui Unknown), length 300

# Router responds to second DHCP request (this time with a slightly longer reply)
06:16:29.299714 IP OpenWrt.lan.bootps > 192.168.1.123.bootpc: BOOTP/DHCP, Reply, length 311

# All sorts of happy things as the laptop gets acquainted...
06:16:29.318846 IP 192.168.1.123 > igmp.mcast.net: igmp v3 report, 1 group record(s)
06:16:29.413109 IP 192.168.1.123.mdns > 224.0.0.251.mdns: 0 [9q] PTR (QM)? _nfs._tcp.local. PTR (QM)? _ipp._tcp.local. PTR (QM)? _ipps._tcp.local. PTR (QM)? _ftp._tcp.local. PTR (QM)? _webdav._tcp.local. PTR (QM)? _webdavs._tcp.local. PTR (QM)? _sftp-ssh._tcp.local. PTR (QM)? _smb._tcp.local. PTR (QM)? _afpovertcp._tcp.local. (141)
06:16:29.510852 IP 192.168.1.123 > igmp.mcast.net: igmp v3 report, 1 group record(s)
06:16:29.573116 ARP, Request who-has OpenWrt.lan tell 192.168.1.123, length 28
06:16:29.575073 ARP, Reply OpenWrt.lan is-at c4:6e:1f:08:c0:bc (oui Unknown), length 28
06:16:29.575082 IP 192.168.1.123.42964 > OpenWrt.lan.domain: 2055+ PTR? 1.1.168.192.in-addr.arpa. (42)
--snip--

```


Just for fun, I tried setting a static IP address and connecting to the router on the 2.4GHz band. I theorized that maybe if I just came in with an IP address and didn't bother asking for one via DHCP, everything would be fine. But no, I'm mostly ignored by the network:

```

06:48:23.547811 IP 192.168.1.8 > 224.0.0.251: igmp v2 report 224.0.0.251
06:48:23.549801 ARP, Reply 192.168.1.8 is-at 00:23:12:04:c4:a9 (oui Unknown), length 28
06:48:23.642853 IP 192.168.1.8.mdns > 224.0.0.251.mdns: 0 [9q] PTR (QM)? _nfs._tcp.local. PTR (QM)? _ipp._tcp.local. PTR (QM)? _ipps._tcp.local. PTR (QM)? _ftp._tcp.local. PTR (QM)? _webdav._tcp.local. PTR (QM)? _webdavs._tcp.local. PTR (QM)? _sftp-ssh._tcp.local. PTR (QM)? _smb._tcp.local. PTR (QM)? _afpovertcp._tcp.local. (141)
06:48:23.686403 ARP, Request who-has 192.168.1.1 tell 192.168.1.8, length 28
06:48:23.730555 IP 192.168.1.8.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? 8.1.168.192.in-addr.arpa. ANY (QM)? petermacbook.local. (96)
06:48:23.981544 IP 192.168.1.8.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? 8.1.168.192.in-addr.arpa. ANY (QM)? petermacbook.local. (96)

```

That's all... I can't ping any remote IPs or browse the web.

But doing the same thing with a static IP and connecting to the 5GHz band, no trouble at all:

```

06:56:45.387767 IP 192.168.1.8 > 224.0.0.251: igmp v2 report 224.0.0.251
06:56:45.389009 ARP, Reply 192.168.1.8 is-at 00:23:12:04:c4:a9 (oui Unknown), length 28
06:56:45.481602 IP 192.168.1.8.mdns > 224.0.0.251.mdns: 0 [9q] PTR (QM)? _nfs._tcp.local. PTR (QM)? _ipp._tcp.local. PTR (QM)? _ipps._tcp.local. PTR (QM)? _ftp._tcp.local. PTR (QM)? _webdav._tcp.local. PTR (QM)? _webdavs._tcp.local. PTR (QM)? _sftp-ssh._tcp.local. PTR (QM)? _smb._tcp.local. PTR (QM)? _afpovertcp._tcp.local. (141)
06:56:45.596002 ARP, Request who-has OpenWrt.lan tell 192.168.1.8, length 28
06:56:45.597482 ARP, Reply OpenWrt.lan is-at c4:6e:1f:08:c0:bc (oui Unknown), length 28
06:56:45.597491 IP 192.168.1.8.33880 > OpenWrt.lan.domain: 20811+ A? daisy.ubuntu.com. (34)
06:56:45.597506 IP 192.168.1.8.18014 > OpenWrt.lan.domain: 64905+ AAAA? daisy.ubuntu.com. (34)
06:56:45.599837 IP OpenWrt.lan.domain > 192.168.1.8.33880: 20811 2/0/0 A 162.213.33.133, A 162.213.33.164 (66)
06:56:45.601228 IP OpenWrt.lan.domain > 192.168.1.8.18014: 64905 0/0/0 (34)
06:56:45.606535 IP 192.168.1.8.38128 > OpenWrt.lan.domain: 49685+ SOA? local. (23)
06:56:45.607516 IP 192.168.1.8.10160 > OpenWrt.lan.domain: 9866+ A? daisy.ubuntu.com. (34)
06:56:45.607547 IP 192.168.1.8.37234 > OpenWrt.lan.domain: 11827+ AAAA? daisy.ubuntu.com. (34)
06:56:45.610350 IP OpenWrt.lan.domain > 192.168.1.8.10160: 9866 2/0/0 A 162.213.33.164, A 162.213.33.133 (66)
06:56:45.610626 IP OpenWrt.lan.domain > 192.168.1.8.37234: 11827 0/0/0 (34)
06:56:45.621772 IP OpenWrt.lan.domain > 192.168.1.8.38128: 49685 NXDomain 0/1/0 (98)
06:56:45.637316 IP 192.168.1.8.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? 8.1.168.192.in-addr.arpa. ANY (QM)? petermacbook.local. (96)

```

Based on this, it seems like DHCP isn't the issue.

I also tried connecting to the router on the 2.4GHz band from **another** Mac desktop I have dual-booting Ubuntu, one that's normally connected via Ethernet. As it turns out, it's not able to connect on this band, either. It has no trouble connecting on the 5GHz band.

So, it's also not just the laptop that's having the problem. I thought that perhaps the router was doing MAC address filtering, even though it's disabled, but since I had this same problem from two different MAC addresses, I don't think that's it.

Here is a table summarizing my results:

[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD]OS[/TD]
[TD]Wifi Band[/TD]
[TD]IP assignment method[/TD]
[TD]Failure[/TD]
[TD]Success[/TD]
[/TR]
[TR]
[TD]Ubuntu 16.04[/TD]
[TD]2.4 GHz[/TD]
[TD]DHCP[/TD]
[TD]X[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Ubuntu 16.04[/TD]
[TD]5 GHz[/TD]
[TD]DHCP[/TD]
[TD][/TD]
[TD]X[/TD]
[/TR]
[TR]
[TD]Ubuntu 16.04[/TD]
[TD]2.4 GHz[/TD]
[TD]Static[/TD]
[TD]X[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Ubuntu 16.04[/TD]
[TD]5 GHz[/TD]
[TD]Static[/TD]
[TD][/TD]
[TD]X[/TD]
[/TR]
[TR]
[TD]Mac OS X 10.7.5[/TD]
[TD]2.4 GHz[/TD]
[TD]DHCP[/TD]
[TD][/TD]
[TD]X[/TD]
[/TR]
[TR]
[TD]Mac OS X 10.7.5[/TD]
[TD]5 GHz[/TD]
[TD]DHCP[/TD]
[TD][/TD]
[TD]X[/TD]
[/TR]
[/TABLE]

In addition, none of the other devices in our house have a problem connecting to either the 2.4GHz or 5GHz bands... we have Mac laptops, Android tablets, iPhones, Roku TVs, and BluRay players all that connect with no problems.

There are a few other things I could try:
1. Flash the router firmware back to TP-LINK stock firmware.
2. Try a different router.

That way, I could determine if the router hardware or OS were at fault. However, I'm skeptical that either one of those could actually be the issue, because:
- If it works on another router, then is it really possible that there's an issue with this router's hardware that causes it specifically not to work with **Ubuntu over the 2.4GHz band**?
- If it works on the same router, then is it really possible that there's an issue with OpenWRT that causes it specifically not to work with **Ubuntu over the 2.4GHz band**?

I suppose it's "possible," but I feel like it would be **extremely** unlikely for a router hardware or router OS problem to exist ***only*** when the combination is Ubuntu + the 2.4GHz band.

Obviously I can still use the 5GHz band, but its reach is not nearly as great as the 2.4GHz band, so it would be ideal if I could get both working.

Any thoughts, comments, suggestions, other diagnostics to try?

EDIT: I should also add that I haven't tried connecting over 2.4GHz from Ubuntu on NON-Apple hardware, so I guess that could also be a possibility... but it seems even more unlikely (Mac hardware + Ubuntu + 2.4GHz band = failure?) And I don't have any non-Apple computers to install Ubuntu on, so I can't test it anyway... ALTHOUGH, I suppose I could try running Ubuntu in VirtualBox from within Mac OS X... now that would be an interesting test... hm..

---

### Post by &amp;KyT$0P# on 2016-07-01
Other than the frequency, is the router configured differently 2.4 GHz vs 5 GHz (or are you just selecting a frequency for the same network)?  I've seen routers that have (effectively) completely different 2.4 GHz and 5 GHz networks...
Also, is Ubuntu using the same NetworkManager connection for your 2.4 GHz and 5 GHz networks?

If the networks are different, make sure your settings in Mac OS X match your settings in Ubuntu.  Given that IP addresses are resolved to a name only in the 5 GHz log, it could be a DNS issue?

>  I thought that perhaps the router was doing MAC address filtering,
Unless you're spoofing MAC address or the like then the fact you can connect fine from Mac OS X on the same computer means it's not this.

> There are a few other things I could try:
1. Flash the router firmware back to TP-LINK stock firmware.
2. Try a different router.
At this point I would think the router isn't the problem, especially since it works with Mac OS X.  tcpdump log from Mac OS X on 2.4 GHz frequency might also be useful for comparison.

> I suppose I could try running Ubuntu in VirtualBox from within Mac OS X... now that would be an interesting test... hm.. 
VirtualBox uses NAT for Internet access, so it basically just uses the host's connection.

---

### Post by Peter_R._Wood on 2016-07-01
> **halogen2 said:**
> Other than the frequency, is the router configured differently 2.4 GHz vs 5 GHz (or are you just selecting a frequency for the same network)?  I've seen routers that have (effectively) completely different 2.4 GHz and 5 GHz networks...

The router has two wireless radios: [TABLE="class: inline, width: 50%"]
[TR="class: row9"]
[TD="class: col0 leftalign"]**Wireless No1:**[/TD]
[TD="class: col1 leftalign"]Atheros AR9340 2.4GHz 802.11bgn[/TD]
[/TR]
[TR="class: row10"]
[TD="class: col0 leftalign"]**Wireless No2:**[/TD]
[TD="class: col1 leftalign"]Atheros AR9582 5GHz 802.11an[/TD]
[/TR]
[/TABLE]

OpenWRT has wireless disabled out of the box, for security, but the first time you turn on, it has some defaults: It has both radios set to broadcast the same SSID, the 2.4GHz on channel 11 and the 5GHz on channel 36, both using 20MHz bandwidth. Wireless encryption is disabled by default. I forget what the transmit power is on each radio by default, but I believe it's set somewhere near the max of what OpenWRT will allow, maybe 20 dBm for 2.4GHz channel 11 and 17 dBm for 5GHz channel 36. By default, OpenWRT has the two radios bridged with the wired lan hardware to create a single local network.

The only changes I have made from the default setup are:
1. Changing the SSIDs from the default same-name, to a unique name for each radio (this has helped me troubleshoot network issues in the past).
2. Setting both to use WPA2 Personal encryption with AES.

You can read a bit more about this particular router model's specs from the OpenWRT perspective here: [https://wiki.openwrt.org/toh/tp-link/tl-wdr3600](https://wiki.openwrt.org/toh/tp-link/tl-wdr3600)

> **halogen2 said:**
> 
Also, is Ubuntu using the same NetworkManager connection for your 2.4 GHz and 5 GHz networks?


No, I have two separate connections, one for the 2.4GHz SSID, one for the 5GHz SSID.

> **halogen2 said:**
> 
If the networks are different, make sure your settings in Mac OS X match your settings in Ubuntu.  Given that IP addresses are resolved to a name only in the 5 GHz log, it could be a DNS issue?


The settings in both Mac OS X and Ubuntu are the same, as best I can tell - both OSs connect to the same SSIDs, and both are set to use DHCP to obtain their IP address, router address, and DNS server addresses. Everything in the "hardware" sections of their wireless settings is also set to "automatic." I don't have any networking parameters input manually (except for when I'm testing the static IP configuration).


> **halogen2 said:**
> Unless you're spoofing MAC address or the like then the fact you can connect fine from Mac OS X on the same computer means it's not this.

No spoofin'...


> **halogen2 said:**
> At this point I would think the router isn't the problem, especially since it works with Mac OS X.  tcpdump log from Mac OS X on 2.4 GHz frequency might also be useful for comparison.


That's a good idea. I can definitely try that and report back.

Thanks for the help!

---

### Post by Peter_R._Wood on 2016-07-01
***So here's something interesting that I just came across.*** From: [https://wiki.openwrt.org/doc/uci/dhcp]("https://wiki.openwrt.org/doc/uci/dhcp?s")

> **Troubleshooting**


**Losing connection due to missing dhcp response when the network is overloaded**

[COLOR=#333333][FONT=Arial]Sometimes when an interface is on the edge of the capacity (especially wifi over longer distances) a [/FONT][/COLOR][COLOR=#333333][FONT=Arial]dhcp[/FONT][/COLOR][COLOR=#333333][FONT=Arial] request could be not replied in time and therefore the [/FONT][/COLOR][COLOR=#333333][FONT=Arial]dhcp[/FONT][/COLOR][COLOR=#333333][FONT=Arial] client will not be able to receive proper network settings. A possible workaround is using static IPs or very long [/FONT][/COLOR][COLOR=#333333][FONT=Arial]dhcp[/FONT][/COLOR][COLOR=#333333][FONT=Arial] leases (more than 12h). This is particularly important when one has several wifi repeaters that use [/FONT][/COLOR][COLOR=#333333][FONT=Arial]dhcp[/FONT][/COLOR][COLOR=#333333][FONT=Arial] and are distant from each other or not easily accessible.[/FONT][/COLOR]

I don't feel like our router's wireless interfaces are "on the edge of capacity," but then again I don't know how one measures that. We have a total of 13 devices connected to the router, 11 using WiFi and 2 using Ethernet. Some are connecting over the 5GHz band (the ones that are closest to the router), but the majority are connecting over the 2.4GHz band. All are obtaining their TCP/IP info settings dynamically via DHCP.

Now I have a theory that the DHCP client in Ubuntu may not be waiting long enough for a response from the DHCP server, and for whatever reason the DHCP server in OpenWRT is somewhat slow to respond when it's contacted through the 2.4GHz connection. If true, perhaps I could adjust the DHCP client settings in Ubuntu to make it wait longer, or I could find out how to tweak the DHCP server in OpenWRT so that it could respond more quickly. That being said, I'm not sure how much more quickly it could respond. Look at the DHCP related syslog entries from both client and server...

Ubuntu during the 2.4GHz connect, politely asking for an address, but then staring staring blankly at OpenWRT as it responds:
```

Jun 29 23:01:32 peter-MacBook dhclient[6232]: DHCPDISCOVER on wls4 to 255.255.255.255 port 67 interval 3 (xid=0x88c21d59)
Jun 29 23:02:03 peter-MacBook dhclient[6242]: XMT: Solicit on wls4, interval 1030ms.

```

OpenWRT during the 2.4GHz connect, repeatedly shouting at Ubuntu, "U CAN HAS 192.168.1.4!!":
```

Wed Jun 29 23:01:32 2016 daemon.info dnsmasq-dhcp[12897]: DHCPDISCOVER(br-lan) 00:23:12:04:c4:a9 
Wed Jun 29 23:01:32 2016 daemon.info dnsmasq-dhcp[12897]: DHCPOFFER(br-lan) 192.168.1.4 00:23:12:04:c4:a9 
Wed Jun 29 23:01:35 2016 daemon.info dnsmasq-dhcp[12897]: DHCPDISCOVER(br-lan) 00:23:12:04:c4:a9 
Wed Jun 29 23:01:35 2016 daemon.info dnsmasq-dhcp[12897]: DHCPOFFER(br-lan) 192.168.1.4 00:23:12:04:c4:a9 
Wed Jun 29 23:01:38 2016 daemon.info dnsmasq-dhcp[12897]: DHCPDISCOVER(br-lan) 00:23:12:04:c4:a9 
Wed Jun 29 23:01:38 2016 daemon.info dnsmasq-dhcp[12897]: DHCPOFFER(br-lan) 192.168.1.4 00:23:12:04:c4:a9 

```

Ubuntu during the 5GHz connect, finally getting the response it's looking for:
```

Jun 29 23:09:25 peter-MacBook dhclient[6640]: DHCPDISCOVER on wls4 to 255.255.255.255 port 67 interval 3 (xid=0x96dbc476)
Jun 29 23:09:25 peter-MacBook dhclient[6640]: DHCPREQUEST of 192.168.1.4 on wls4 to 255.255.255.255 port 67 (xid=0x76c4db96)
Jun 29 23:09:25 peter-MacBook dhclient[6640]: DHCPOFFER of 192.168.1.4 from 192.168.1.1
Jun 29 23:09:25 peter-MacBook dhclient[6640]: DHCPACK of 192.168.1.4 from 192.168.1.1

```

OpenWRT during the 5GHz connect, relieved that it can now hold a proper conversation with Ubuntu:
```

Wed Jun 29 23:09:25 2016 daemon.info dnsmasq-dhcp[12897]: DHCPDISCOVER(br-lan) 00:23:12:04:c4:a9 
Wed Jun 29 23:09:25 2016 daemon.info dnsmasq-dhcp[12897]: DHCPOFFER(br-lan) 192.168.1.4 00:23:12:04:c4:a9 
Wed Jun 29 23:09:25 2016 daemon.info dnsmasq-dhcp[12897]: DHCPREQUEST(br-lan) 192.168.1.4 00:23:12:04:c4:a9 
Wed Jun 29 23:09:25 2016 daemon.info dnsmasq-dhcp[12897]: DHCPACK(br-lan) 192.168.1.4 00:23:12:04:c4:a9 petermacbook

```

Granted, I don't have sub-second logging available, but less than a second seems plenty fast for a DHCP server to respond. Could Ubuntu be more picky about DHCP server response time, down to a matter of milliseconds? Or for some reason it likes the offer it's getting when the response comes over the 5GHz band versus the 2.4GHz band? Since there's not a record, per se, of Ubuntu "refusing" the DHCP offer, I'm not sure about that one.

So, my three to-do items are:
1. Get tcpdump from Mac during successful 2.4GHz connect.
2. Tweak Ubuntu DHCP client so it waits longer for DHCP response (if possible).
3. Investigate how to performance tune OpenWRT's DHCP server (i.e. dnsmasq).

---

### Post by jeremy31 on 2016-07-01
*Thread moved to **Apple Hardware Users**.*

---

### Post by &amp;KyT$0P# on 2016-07-01
If I'm understanding this correctly there should a relatively simple way to check if you're overloading the router/network.  Disconnect all devices from the router (both Ethernet and Wi-Fi), then try again to connect a Mac w/ Ubuntu over the 2.4 GHz frequency.  Surely one single device can't be too much for it to handle, right? :-k

For what it's worth, something I've noticed on my own Mac (which also used to run OS X 10.7.5), it seems that Mac OS X is significantly more sensitive of Wi-Fi than Ubuntu.  (This is at least with a network I *know* is 2.4 GHz.  I have no idea about 5 GHz network.)
So make sure you're in relatively close proximity to the router while testing.

---

### Post by Peter_R._Wood on 2016-07-01
> **halogen2 said:**
> If I'm understanding this correctly there should a relatively simple way to check if you're overloading the router/network.  Disconnect all devices from the router (both Ethernet and Wi-Fi), then try again to connect a Mac w/ Ubuntu over the 2.4 GHz frequency.  Surely one single device can't be too much for it to handle, right? :-k

You've got a point! I may have a chance to do that in a little while...

---

### Post by Peter_R._Wood on 2016-07-01
I got tcpdump data from the laptop when it's booted into Mac OS X, successfully connects to the 2.4GHz network:
[https://gist.github.com/prwood/4ea37ece1a2b46210cbdc2388076ecd6](https://gist.github.com/prwood/4ea37ece1a2b46210cbdc2388076ecd6)

verbose tcpdump from Ubuntu when it's trying to connect to OpenWRT:
[https://gist.github.com/prwood/8f80229ddf5299ff29e9485a0e4c9b86](https://gist.github.com/prwood/8f80229ddf5299ff29e9485a0e4c9b86)

verbose tcpdump from OpenWRT when it's trying to help Ubuntu get connected:
[https://gist.github.com/prwood/1b684452c098d9fa932cd5855335e0de](https://gist.github.com/prwood/1b684452c098d9fa932cd5855335e0de)

verbose tcpdump from a third, observer laptop running Mac OS X, watching the chatter between Ubuntu and OpenWRT:
[https://gist.github.com/prwood/1ecbc61955badccdc39a2e38f6951406](https://gist.github.com/prwood/1ecbc61955badccdc39a2e38f6951406)

One thing I notice is that when OpenWRT responds Ubuntu's DHCP request, it includes the following:

```

OpenWrt.lan.bootps > prw-macbook-late2008.lan.bootpc:** [bad udp  cksum 0x8512 -> 0x6106!]** BOOTP/DHCP, Reply, length 300, xid  0x3a0c9913, Flags [none] (0x0000)

```

I'm wondering if 'bad udp cksum' is normal, or if it's worth investigating. Here is one mention that I found that specifically mentions Ubuntu clients and a dnsmasq DHCP server, which is what OpenWRT uses:

[https://github.com/projectcalico/calico/issues/40](https://github.com/projectcalico/calico/issues/40)

However, it seems related to the virtual machines they're working with, so I'm not sure how applicable it is to my case. Anyway, it's probably worth investigating further.

---

### Post by Peter_R._Wood on 2016-07-04
Further testing - I reverted the router back to its stock (TP-LINK branded) firmware, and I still had issues with my connection in Ubuntu, but this time it was slightly different:

[https://gist.github.com/prwood/b05822b36ae930923f5c8f7f4cb04f6d](https://gist.github.com/prwood/b05822b36ae930923f5c8f7f4cb04f6d)

This time, the DHCP request and reply were sent and received successfully, but after the DHCP reply, the Ubuntu client continuously issues an ARP request. It looks like it's trying to find the router again...

```

08:05:29.917767 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.0.1 tell 192.168.0.102, length 28
--etc etc more lines the same--

```

I took a quick look at the DHCP client config in Ubuntu and I didn't see anything that seemed like it could help, but I will need to take a second, more thorough look...

Ugh... not sure what else to look at, at this point.

---

### Post by Peter_R._Wood on 2016-07-04
> **halogen2 said:**
> If I'm understanding this correctly there should a relatively simple way to check if you're overloading the router/network.  Disconnect all devices from the router (both Ethernet and Wi-Fi), then try again to connect a Mac w/ Ubuntu over the 2.4 GHz frequency.  Surely one single device can't be too much for it to handle, right? :-k

Just an update, I did try this - I created new WiFi ssids and verified that none of the clients were reconnecting, and then tried to connect with the Ubuntu laptop using the 2.4GHz channel. I got the same response as before - Ubuntu tries to connect and then ignores the DHCP responses from OpenWRT. So, it doesn't seem to be related to the capacity of the router to be able to handle a larger number of clients.

---

### Post by Peter_R._Wood on 2016-07-04
I've also tried removing and reinstalling the proprietary Broadcom drivers for the wireless card in this laptop, to no effect. It appears that there aren't any open source drivers available for this particular chipset:

```

02:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
    Subsystem: Apple Inc. AirPort Extreme
    Physical Slot: 4
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
    Region 2: Memory at d0000000 (64-bit, prefetchable) [size=1M]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [d0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM not supported, Exit Latency L0s <4us, L1 <64us
            ClockPM- Surprise+ LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [13c v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number c4-a9-12-ff-ff-04-00-23
    Capabilities: [16c v1] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: ssb, wl

```

However, I have the same problem if I try to connect to wireless from another Mac running Ubuntu. This Mac normally is connected with Ethernet, so it's not as much of a concern. So 

```

02:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Apple Inc. AirPort Extreme
    Physical Slot: 1
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at 90100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <512ns, L1 <64us
            ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [90] MSI-X: Enable- Count=1 Masked-
        Vector table: BAR=0 offset=00000000
        PBA: BAR=0 offset=00000000
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Kernel driver in use: ath5k
    Kernel modules: ath5k


```

Since there are two different chipsets and two different drivers here, and both are having problems. I'm guessing it's not the chipset or the driver that's the problem.

---

### Post by Peter_R._Wood on 2016-07-11
I'm back, with an update! So it seems that the problem lies in the proprietary Broadcom driver in Linux, which is the one I had originally chosen to install. With this driver, I'm able to connect to the 5GHz band with no problems, but with the 2.4GHz band I can't get any connectivity.

However, if I switch to the open source b43 driver, everything works fine, and I'm able to get connectivity either on the 2.4GHz or the 5GHz band. The only issue is that with the open source b43 driver, it doesn't seem to support 40MHz bandwidth on the 5GHz band. If I switch back to the proprietary driver, I can utilize 40MHz bandwidth on the 5GHz band, but I still have the issue with connectivity on the 2.4GHz band.

So I guess my choice right now is full connectivity (but no 40Hz bandwidth) on both bands with the open source driver, or full connectivity on the 5GHz band only, with 40MHz bandwidth on the proprietary driver. For the moment I'll choose full connectivity and go with the open source driver. However, I'd love to have support for 40MHz bandwidth, so if anybody knows how to get that to work with the open source driver, I'd love to hear i!

---

### Post by Peter_R._Wood on 2016-07-13
I'm hoping to reframe this thread, as I've refined my analysis a bit since my original post. :)

I'm hoping that this can be moved back to the networking/wireless forum, as it seems to have more to do with wireless hardware and drivers than it does with Mac hardware specifically (this same controller is used in some HP laptops apparently - [https://www.amazon.com/HP-Broadcom-Bcm4321-Wireless-300mbps/dp/B008FUG8XU](https://www.amazon.com/HP-Broadcom-Bcm4321-Wireless-300mbps/dp/B008FUG8XU) )

I have a Mac laptop with a Intel Core 2 Duo processor that has a Broadcom BCM4321 wireless controller. It is dual-booting Mac OS X 10.7.5 and Ubuntu 16.04. My router is a TP-Link TL-WDR3600 running OpenWRT 15.05.1. It supports 802.11a/b/g/n and has two separate radios for the 2.4GHz and 5GHz bands.

Connecting from Mac OS X, the laptop is able to authenticate using WPA2, obtain an ip address, and get 802.11n speeds on both the 2.4GHz and 5GHz bands.

Connecting from Ubuntu 16.04 using the Broadcom proprietary driver, the laptop is able to authenticate using WPA2 on both the 2.4GHz and 5GHz bands. On the 5GHz band, it is able to obtain an IP address and get 802.11n speeds. On the 2.4GHz band, it is not able to obtain an IP address or get any network connectivity of any form, beyond just authenticating.

Connecting from Ubuntu 16.04 using the b43 open source driver, the laptop is able to authenticate using WPA2 and obtain an IP address on both the 2.4GHz and 5GHz bands. However, on both the 2.4GHz and 5GHz bands, it's not able to obtain 802.11n speeds. It appears to be limited to 802.11g speeds in the 2.4GHz band and 802.11a speeds in the 5GHz band.

Any thoughts on why the two Linux drivers apparently have their own unique problems with this card? Is it just not well-supported? I'm good with the proprietary driver on the 5GHz band, provided I keep my laptop in range of the router, but I'd like to be able to roam further on the 2.4GHz band while still maintaining 802.11n speeds.

---

