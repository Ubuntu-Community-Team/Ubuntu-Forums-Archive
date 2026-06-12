---
title: "wireless setup Surecom"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Fakircho on 2007-07-15
I have a Surecom EP 9001g USB dongle 

I think a managed to install it using ndiswrapper.  
ndiswrapper -l gives me 

netrtuw : driver installed
device (0769:11F2) present

iwconfig gives me

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:"MacBook 1" Nickname:"MacBook 1"
Mode:Ad-Hoc Frequency:2.462 GHz Cell: 32:40:88:13:82:9C
Bit Rate=54 Mb/s Tx-Power:20 dBm Sensitivity=0/3
RTS thr=2432 B Fragment thr=2432 B
Power Managementff
Link Quality:65/100 Signal level:-54 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I can not connect to my other PC running XP and using the same USB adapter. The XP machine connects to my wife's MacBook via wireless no problem. 

I have posted in the wireless forum but i have not got a single reply. Where do i go from here i am really frustrated and i have read thread after thread for a few days now. 

Please help.

---

### Post by Fitzy_oz on 2007-07-16
> **Fakircho said:**
> I have a Surecom EP 9001g USB dongle 

I think a managed to install it using ndiswrapper.  
ndiswrapper -l gives me 

netrtuw : driver installed
device (0769:11F2) present

iwconfig gives me

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:"MacBook 1" Nickname:"MacBook 1"
Mode:Ad-Hoc Frequency:2.462 GHz Cell: 32:40:88:13:82:9C
Bit Rate=54 Mb/s Tx-Power:20 dBm Sensitivity=0/3
RTS thr=2432 B Fragment thr=2432 B
Power Managementff
Link Quality:65/100 Signal level:-54 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I can not connect to my other PC running XP and using the same USB adapter. The XP machine connects to my wife's MacBook via wireless no problem. 

I have posted in the wireless forum but i have not got a single reply. Where do i go from here i am really frustrated and i have read thread after thread for a few days now. 

Please help.

I'll do my best,
First up, is there an adsl mode anywhere involved in this, if there is, is it handing out the Ip addresses?

---

### Post by Fakircho on 2007-07-17
Hi Fitzy_oz

Thanks for the reply. I am not sure what you mean by "adsl mode" but I have ADSL through my network card eth0. For some reason when Ubuntu starts up i have to manually run sudo dhclient in order to obtain an ip lease for my eth0 in order form my internet to work. It does not give my wireless an IP address. If i run sudo dhclient wlan0 it just goes through some lines and says that it can not get an Ip address. I hope i am being clear :) let me know what information i need to supply form here on.

---

### Post by Fitzy_oz on 2007-07-17
> **Fakircho said:**
> Hi Fitzy_oz

Thanks for the reply. I am not sure what you mean by "adsl mode" but I have ADSL through my network card eth0. For some reason when Ubuntu starts up i have to manually run sudo dhclient in order to obtain an ip lease for my eth0 in order form my internet to work. It does not give my wireless an IP address. If i run sudo dhclient wlan0 it just goes through some lines and says that it can not get an Ip address. I hope i am being clear :) let me know what information i need to supply form here on.

Sorry mate, I'd had way too much coffee, I meant an ADSL router which you have pointed out goes through you're wired ethernet adapter, not the wireless. Near as I can tell all you really need to do is to bridge the wireless and ethernet connections similar to the way you would in windows if you had two network adapters.  

Try the following -
Drop to a terminal and type the following:

sudo apt-get install bridge-utils uml-utilities  #Install the network bridge utilities
sudo brctl addbr br0                                      #Create the bridge, it's effectively another network interface
sudo ifconfig eth0 0.0.0.0 promisc               # Puts the Ethernet interface in prmoiscuous mode
sudo ifconfig wlan0 0.0.0.0 promisc             # Puts the wireless interface in promiscuous mode
sudo brctl addif br0 eth0                              # Adds the ethernet adapter to the bridge
sudo brctl addif br0 wlan0                            # Adds the wireless adapter to the bridge
sudo dhclient br0                                          # Obtains and IP address for the network bridge

Now in theory you should be able to see everything on the network form that pc regardless of whether it's thorugh the wired connection or wireless it should be able to resolve the pcs now.

Hope that helps.

---

### Post by Fakircho on 2007-07-18
I am gonna ask a stupid question. What does bridging do? Is kind of sharing the connections? 

Lets put the internet - wired connection aside for now. 

For now i just want to be able to find out if my wireless dongle is correctly installed and configured in order to connect to the XP computer. 
I do not want to share the internet connection at this point. 

Are there any configurations i need to perform to the wireless adapter in order for it connect to XP. When i run wifi radar i can see the connection and the name i have given it but wifi radar can not get an IP??? if i boot up both machines into Windows then they connect. I just want to do the same but with one computer running XP and the other UBUNTU. 

Does this make sense?

---

