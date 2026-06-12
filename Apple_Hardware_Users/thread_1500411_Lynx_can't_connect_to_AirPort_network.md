---
title: "Lynx can't connect to AirPort network"
date: 2010-06-03
forum: Apple Hardware Users
---

### Post by pkganesh123 on 2010-06-03
Hello,

I have a Lenovo G 430 3000 Laptop running Lucid Lynx, and also an iMac Desktop running SL 10.6.3. My problem is that I can't get Laptop connected to iMac when iMac is running a computer-computer AirPort network. Here are extra details:

1.My Laptop has a Broadcom Wireless Card, and I've installed fwcutter as well as wireless drivers suggested by System>Administration>Hardware Drivers. Earlier my laptop was running Jaunty and it worked fine. Also, earlier the Laptop had Windows XP as a dual-boot option , and XP used to connect faultessly.  

2. Here's an excerpt from tail /var/log/syslog as I attempt to connect to mac.homenet.com (Airport n/w): 
:------------------------------------------
Jun  3 14:29:31 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Jun  3 14:29:50 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun  3 14:29:57 ubuntu dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun  3 14:29:59 ubuntu NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
Jun  3 14:29:59 ubuntu NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 1800
Jun  3 14:29:59 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun  3 14:29:59 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun  3 14:29:59 ubuntu NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)
Jun  3 14:29:59 ubuntu NetworkManager: <info>  Activation (eth1) failed for access point (mac.homenet.com)
Jun  3 14:29:59 ubuntu NetworkManager: <info>  Marking connection 'Auto mac.homenet.com' invalid.
Jun  3 14:29:59 ubuntu NetworkManager: <info>  Activation (eth1) failed.
Jun  3 14:29:59 ubuntu NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun  3 14:29:59 ubuntu NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Jun  3 14:29:59 ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Jun  3 14:29:59 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jun  3 14:29:59 ubuntu wpa_supplicant[867]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

---------------------------
In this case, Airport was running an IPv4 network(no authentication), configured with DHCP, and a DHCP-assigned address. I have installed wpa_supplicant  on Laptop.

3. My Laptop can however, connect to other unprotected networks in my neighbourhood without any issues.

4. If I instead start a network on Laptop, and try to connect to it from iMac, I get a timeout error consistently. This again used to be no problem with the earlier Jaunty.

 
Any suggestions?
--Ganesh

---

