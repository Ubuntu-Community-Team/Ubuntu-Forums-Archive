---
title: "What are IPv6 Routers"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by Alanmw on 2005-08-15
I put this in the Live CD forum with no luck. Perhaps I will have more here. 
The HH LiveCD boots and starts Ubuntu fine but after configuring then network card, a D-Link DWL-AB520, which is picked up by the system I cannot connect to our home wireless-network.
route -n just shows the Headings and dmesg shows the following last 3 lines :-

IPv6 over IPv4 tunneling driver
ath0: No IPv6 routers present
ath0: No IPv6 routers present

I am very new to Linux and do not know where to go from here. A search of the forums did not bring up anything useful either.
Any ideas please.

Alan

---

### Post by KingBahamut on 2005-08-15
Hmmmm...
Atheros Driver, probably not picked up by the OS. 

Ive never had much luck with Dlink Wireless devices. I do know that the Multi-Atheros project doesnt have any drivers out for it as im aware.  I think there is a project page over at Sf.net.

If your going to use wireless devices with Linux, stay with Prism2 based cards...they are clearly the safest and easiest to work with.

---

### Post by KingBahamut on 2005-08-15
If its not on this list, you dont want it. 

If it is on the list and supported you do want it. 

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by wmcbrine on 2005-08-15
Just to add, IPv6 is (almost certainly) not your problem. Those messages are normal. Only a handful of people are actually on IPv6 networks. (I'd really have preferred it if Ubuntu didn't enable IPv6 by default, as it caused me some DNS slowness until I disabled it.)

---

### Post by blair on 2005-08-15
IPv6 is the next generation version of IP. It has actually been around for about 10 years but seen very little adoption to date. Its biggest claim to fame is a few more bytes for source address and destination address fields. This makes it possible to support literally trillions of IP-addressable devices, vice the mere millions supported in the mainstream version of IP in use today, which is generally known as IPv4. IPv6 also has many other features/enhancements over IPv4 as well. 

Forward looking Linux distros may naturally include support for IPv6. It is possible that your PC when it issued a DHCP request to your router/DHCP server it asked for a IPv6 address. It is unlikely any consumer-grade or low end router would support this at this time. I would expect that if this was indeed what happened, that the Linux box would have subsequently issued a DHCP address request for a standard IPv4 address, which your router would have responded to.

---

### Post by Alanmw on 2005-08-16
Does that mean that I will have to go back to Old Reliable Windows again?

---

### Post by poofyhairguy on 2005-08-16
[QUOTE=Alanmw]Does that mean that I will have to go back to Old Reliable Windows again?[/QUOTE]

Maybe. Does the network tool tell you you cannot activate the connection?

---

### Post by Alanmw on 2005-08-16
Hi
   No. The Configuration goes ahead perfectly and says it is done at the end. That is what puzzles me.
  "iwconfi" shows the ESSID and the KEY correctly but "route -n" only shows the headings and no results.
  "dhclient" also says there is nothing. I don't remember exactly what the results were. I cannot ping the router or other computers on the LAN.
   Is that any use to help solve the problem?

Alan

---

### Post by varunus on 2005-08-17
OK, so it looks like you're having some problems with routes...

Here's what you should do:

Open up a terminal and type:
```
sudo iwconfig ath0 essid SSIDOFROUTER
```
Replace that with the router's name that the windows wireless panel shows.

This tells your wireless card to connect to that router.  Type in "iwconfig" now and hit enter.  You should see ```
something like this:
lo        no wireless extensions.

ath0      IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:2D:D3:2C
          Bit Rate=11 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/94  Signal level=-55 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:30  Invalid misc:30   Missed beacon:4

eth0      no wireless extensions.

sit0      no wireless extensions.
```

The key thing to look for here; what does the "Access Point:" say?  If it is all zeros or all F's, you have a problem.  Post back here if that is the case.

If this works, try typing "sudo dhclient ath0" in the terminal.  You should get something like this:
```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:90:96:8b:02:5c
Sending on   LPF/ath0/00:90:96:8b:02:5c
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.118 -- renewal in 32525 seconds.
```

This assigns your computer an IP address.  If this works, post back, if it just times out (this command should only take a few seconds), then also post back.

If this works, try typing "ping 64.233.161.99" in the terminal.  Does this work?  Also try "ping www.google.com" in the terminal.  Does this work?

Good luck, and post back here...

---

### Post by Alanmw on 2005-08-21
ath0      IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:2D:D3:2C
          Bit Rate=11 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/94  Signal level=-55 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:30  Invalid misc:30   Missed beacon:4

eth0      no wireless extensions.

sit0      no wireless extensions.[/CODE]

The key thing to look for here; what does the "Access Point:" say?  If it is all zeros or all F's, you have a problem.  Post back here if that is the case.


This is the result of "iwconfig" :-

I am afraid the "Access Point:" is all F's but the essid and the WEP are correct.

"dhclient" ends up with:-
No DHCPOFFERS received
No working lease in persistent database - sleeping

"route -n" only shows the various headings but no results.

I hope this is of use in solving the problem.

Thanks     Alan

---

### Post by varunus on 2005-08-23
Hmm...

It seems that the computer is not seeing the router correctly...Even after typing in the correct SSID.

Can you try typing:
```
sudo iwlist ath0 scan
```

This will list a bunch of access points you can connect to.  Look for the **:**:**:**:** code for yours, and enter it by doing the following:

```
sudo iwconfig ath0 ap **:**:**:**:**
```

Also, try disabling WEP and connecting.  If that works, then its a WEP problem...that can be fixed for most cards.

---

### Post by Alanmw on 2005-08-23
Hi 
I am afraid 'sudo iwlist ath0 scan' does not work - comes up with 'no scans'.

What do I do now? 

Do I try connecting with the WEP off and see what the result is?

Thanks   Alan

---

### Post by varunus on 2005-08-26
Yeah, try connecting with WEP off and see if that works.  If it does, we can go from there.

"sudo iwlist ath0 scan" comes up with no scans?  Weird...Is your router set to broadcast?

---

### Post by Alanmw on 2005-09-01
I have found the problem!!! It is to do with the LiveCD. It must have a glitch and will not connect the card. In our country we have ADSL but it is very expensive and has a limit to the amount of usage per month but on the last night of the month you can go over the limit with out getting cut off!!! I downloaded the Instalation CD and have just installed HH 5.04 with very little trouble. The network section tried to use DHCP but failed and asked for my actual IP address and that was it. I am on line now using HH and writing this now.
Thanks for all your help in trying to get the problem solved. I will now go and explore more of the system. Once again many thanks.

---

