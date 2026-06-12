---
title: "Network Config"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Eldon on 2005-10-08
Noob disclaimer: First time with Ubuntu and pretty much to Linux too.  Your post can't be dumbed down enough, don't worry about talking down to me ;) 

I've got Ubuntu up and running with a shocking amount of ease.  Kudos to the community.  So far it looks like the only problem is getting onto the net.  I'm using an older P4 with an Asus P4B motherboard and 3Com 3C-905B-TX network card.  The card was not detected during setup so I chose "configure network later".  Once the desktop was up I went to System -> Device Manager and almost fell out of my chair when I saw it was detected.  (I have never seen an OS able to detect this card.)  But still no internet.

-I am behind a D-link router whose "cable test" app says the Linux box is connected.
-The 3Com link light is on and goes off with cable disconnect.  I've used this cable/card a lot before and I'm not going to rule it out but would be awfully surprised to find out its a hardware fault.
-I have gone into System->Network and enabled the connection.  It is currently set to DHCP with no DNS servers listed.  I believe IPv6 is still enabled (I don't know how to confirm this) as per [this]("http://ubuntuforums.org/showthread.php?t=72963") thread and I don't know how to disable it.
-I have done sudo pppoeconf and get:
"Sorry i scanned 1 interface but the access concentrator of your provider did not respond. please check your network and moderm cables. another reason for the scan failure may also be another running ppoe process which controls the modem."
-I have tried (and since undone) the fix suggested [here]("http://ubuntuforums.org/showthread.php?t=72963&page=2") which is to comment out the proxyarp in /etc/ppp/options
-I can ping localhost however pinging my router gives "destination host unreachable".  As best I can tell the NIC is not getting a reply from its DHCP calls.  I found this in Applications -> system tools -> system logs
daemon.log - dhcpdiscover on eth0 to 255.255.255.255 port 67 interval XX
(xx is 5,13,19,10,14)
-then No DHCP Offers received
-then No working leases in persistent database - sleeping
-then rinse and repeat.

kern.log - NETDEV Watchdog: eth0: transmit timed out
-eth0: transmit timed out, tx_status 00 status e000
diagnostics: net 0cd8 media 8880 dma 00000a0 fifo 8000
-Flags; bus-master 1, dirty 0(0) current 16(0)
transmit list 1e209200 vs. df209200
then it looks like 15 different packet entries?
then eth0: resetting the Tx ring pointer.

-I've tried a valid static IP and defined the DNS servers, no go there either.
-I have rebooted (now there's something you don't often see on linux forums)

Thats about all I can think of, any ideas?
Thanks

---

### Post by Eldon on 2005-10-08
I just put a second NIC (3C-905C) with a second cable in the box, both are detected and enabled and I've tried setting each to the default gateway with no luck.  
Going to Applications->system tools->network tools brings up the network tool.  Then on the Devices tab when I select eth0 or eth2 (I don't know why the second didn't show up as eth1 but there's only the 2 cards in there) it only shows the IPv6 protocol.  The loopback device shows both IPv4 and IPv6.  Is this because DHPC isn't working on the cards to assign an IPv4 IP or do I somehow need to enable IPv4 (and maybe disable IPv6) on them?

---

### Post by Eldon on 2005-10-08
When booting the system hangs at "configuring network" but eventually comes up with "ok", then hangs at "waiting for network to come up" which eventually fails.

Pulled out both cards, rebooted, put in the 905-c only, rebooted.  now it works.    Thats that I guess

---

