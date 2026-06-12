---
title: "Wireless Help"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by jeric2k5 on 2007-03-23
Ok so I recently installed Ubuntu 6.10 from the Live CD and I'm having some issues with the my wireless internet card. My wireless adapter is the D-Link DWL-G510 and before it was working great with my Windows XP Media Edition but it is not recongized in Ubuntu. I tried using Ndiswrapper but when the driver is installed Ndiswrapper says no hardware for the driver is present. The funny thing is though when I go to Wireless Tools I get three different Network Devices and it seems that the wireless adapter is working. 

The first Network Device is "Loopback interface (lo)" -non configurable- the second one is an "Unknown interface (wifi0)" -non configurable-, and the third device is an "Unknown interface (ath0)". The Loopback interface and the Unknown interface (ath0) both contain IP Information but Unknown interface (wifi0) does not have any preset IP information. Now here is the funny thing, "Unknown interface (wifi0)" shows that there are bytes being transmitted and the interface is also receiving bytes at a constant pace. I'm thinking that the wireless is working but it isnt configured right but on the network tools only "unknown interface (ath0)" is configurable with the Wireless connection in the Network Settings. Is there anyway I can change these two so that I will get internet or any other way I can configure my card to work? 

I love Ubuntu and I just need internet now via the wireless card since I use the wireless connection from upstairs in my house. I don' have a connected connection so anything I have to install must be manually downloaded from a separate computer and placed on Ubuntu. Any help will be great. Thanks :-D!

---

### Post by Bachstelze on 2007-03-23
Open up a terminal and do 

```
sudo iwconfig
```

then paste what you get.

---

### Post by jeric2k5 on 2007-03-23
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Casa Networking"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by Bachstelze on 2007-03-23
Hmm, your wireless interface is detected and has an ESSID configured. What happens when you do *sudo dhclient ath0* ?

---

### Post by jeric2k5 on 2007-03-24
So I ran sudo dhclient for both wifi0 and ath0 and both returned the same message "No DHCPOFFERS received, No working leases in persistent database - sleeping" If wifi0 isnt working why is it receiving and sending packets? Anything for me to do?

Thanks for the help by the way, :-)

---

