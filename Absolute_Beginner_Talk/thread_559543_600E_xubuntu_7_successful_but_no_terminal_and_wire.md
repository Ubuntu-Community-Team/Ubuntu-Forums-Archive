---
title: "600E xubuntu 7 successful but no terminal and wireless"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by freescale42 on 2007-09-25
just installed xubuntu 7 on thinkpad 600e and runs fine except there is no terminal program - super user mode and when I try to add/remove programs it requests internet access which I don't have up and running yet.  
I need terminal mode to run commands to debug my wireless connection which is Cisco Aironet 350 and when i go to network it shows:
Wireless connection (wifi0) and Wireless Connection (eth0) and I set up the SSID identical to my router with dhcp and no connection.  

Any advise on how to install terminal and debug wireless connection would be appreciated.
Thanks

---

### Post by por100pre1 on 2007-09-25
Weird. Try pressing Alt+F2 and then type:

```
xfce4-terminal
```

---

### Post by overdrank on 2007-09-25
> **freescale42 said:**
> just installed xubuntu 7 on thinkpad 600e and runs fine except there is no terminal program - super user mode and when I try to add/remove programs it requests internet access which I don't have up and running yet.  
I need terminal mode to run commands to debug my wireless connection which is Cisco Aironet 350 and when i go to network it shows:
Wireless connection (wifi0) and Wireless Connection (eth0) and I set up the SSID identical to my router with dhcp and no connection.  

Any advise on how to install terminal and debug wireless connection would be appreciated.
Thanks

HI you have no terminal located under applications,accessories,terminal? What happens when you use the ctrl,alt,F1 keys at the same time? To return to GUI use the ctrl,alt,F7 keys.

---

### Post by freescale42 on 2007-09-25
Thanks, alt+F2 followed by xfce4-terminal did the trick for the terminal.  Now i'm working on getting my wireless working which is a Cisco Aironet 350 and the router is Belkin.  When I run lshw the network shows
desciption: Wireless interface
physical id: 1
logical name: eth0
serical: 00:0d:65:ca
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

I followed this by the cmd sudo pccardctl ident which returned
Socket 1: 
product info: "CISCO Systems", "350 Series Wireless LAN Adapter", "", "" 
manfid: 0x015f, 0x000a
function: 6 (network)

i ran iwconfig with the following results
eth0 IEEE 802.11-DS ESSID: "freescale"
Mode:Managed Frequency:2.412 GHz Access Pount: 00:11:50:67:
Bit Rate:11MB/s Tx-Power:20 dBm Sensitivity=0/65535
Retry limit: 16 RTS thr:off Fragment thr: off
Power Management:off
link Quality=100/100 Signal level=-32dBm Noise level=-88dBm
Rx invalid nwid:3 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:144671 Missed beacon:0

wifi0 IEEE 802.11-DS ESSID: "freescale"
Mode:Managed Frequency:2.412 GHz Access Pount: 00:11:50:67:
Bit Rate:11MB/s Tx-Power:20 dBm Sensitivity=0/65535
Retry limit: 16 RTS thr:off Fragment thr: off
Power Management:off
link Quality=100/100 Signal level=-32dBm Noise level=-88dBm
Rx invalid nwid:3 Rx invalid crpyt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:144671 Missed beacon:0

I've tried to ping my router and destination host unreachable.

---

### Post by overdrank on 2007-09-25
Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=488300&highlight=Cisco+Aironet+350](http://ubuntuforums.org/showthread.php?t=488300&highlight=Cisco+Aironet+350)
and if you care to see other thread on that card 
[http://ubuntuforums.org/search.php?searchid=27746390](http://ubuntuforums.org/search.php?searchid=27746390)
Good luck!

---

### Post by freescale42 on 2007-09-27
I had my Aironet card plugged into the second PCMCIA slot and I moved it to the first slot and rebooted, now works.

---

### Post by overdrank on 2007-09-27
> **freescale42 said:**
> I had my Aironet card plugged into the second PCMCIA slot and I moved it to the first slot and rebooted, now works.

Great glad to hear. Good luck and could you mark this thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

