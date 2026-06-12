---
title: "Wireless connection just died"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Radovitch on 2007-02-14
Hi, After months of flawless connection the wireless node on my network (Dapper Drake) has suddenly gone dead on me. As of this morning when I turned on the PC. The Windows half of the dual boot works ok so I know it's not a hardware problem. When I booted up I saw that the network connection button was crossed out. Network settings informs me that the wlan0 interface is active. I have a static IP with a WPA-PSK keyed router. The only recent change I made was installing Webmin though that was two days ago. No doubt I need to supply further information here but being a Linux newbie I"m not sure what's needed. This is the ifconfig wlan0:

Link encap:Ethernet  HWaddr 00:12:BF:1C:34:0C
inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::212:bfff:fe1c:340c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)

and the iwconfig:

IEEE 802.11g  ESSID:off/any
Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
Bit Rate:2 Mb/s   Tx-Power:19 dBm
RTS thr:2347 B   Fragment thr:2346 B
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Troubled on 2007-02-14
Try running 'sudo dhclient'; it works for me on occasion.

---

### Post by meborc on 2007-02-14
if you try 
```
sudo ifdown wlan0
sudo ifup wlan0
```
what happens?

---

### Post by MCSE_Crossover on 2007-02-14
> **Troubled said:**
> Try running 'sudo dhclient'; it works for me on occasion.

It states that he has a static IP address, so this shouldn't make difference, although this is usually what does it for me as well.

What I did to resolve this was add an entry to /etc/network/interfaces I believe that tells wlan0 to autoconfig dhcp upon boot.

Not sure why this user would be having the issues with his static address and wlan at this point though...I would assume something with recent changes or additions of software...

---

### Post by liquidslam on 2007-02-14
The sudo if down and ifup commands don't do anything. The cursor just flashes for a few seconds and then goes back to the prompt. I'm inclined to suspect that MCSE Crossover might be right as regards recent changes or additions of software except that I haven't done any in the last couple of days.

---

### Post by MCSE_Crossover on 2007-02-14
> **Troubled said:**
> Try running 'sudo dhclient'; it works for me on occasion.

Can you ping your router? How are you accessing the internet now? Do you have a second computer? Is it static as well? Have you created a reservation for your static IP address? Is your router running DHCP? Do you have security and have you checked your DHCP table to ensure that no one is sitting on your line using that IP address?

try /usr/local/etc/webmin stop or wherever that program is located. Kill webmin, sudo ifdown && sudo ifup and see if anything clears up.

---

### Post by liquidslam on 2007-02-14
Negative on the router ping. I have two computers on my LAN. The first has an ethernet connection via the modum/wireless/router and the second is the one with the Ubuntu problem. The router was initially set for DHCP but sometime ago I changed the connections on both computers to static. Can you tell me what you mean by 'creating a reservation for the static IP address'? I stopped the webmin process though I am not sure how to do this with regard to sudo ifdown and ifup. As for security I have a WPA key with AES encryption. By the way, why do I get no reactions at all when using the sudo ifdown wlan0 and ifup commands? 
After rebooting I see the situation has not changed.

---

