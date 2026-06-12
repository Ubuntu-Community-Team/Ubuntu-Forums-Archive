---
title: "cant join wpa encrypted network"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by jimmybt on 2007-04-26
Hi all
I installed feisty on my laptop partitioned with windows. Am on a wireless network using WPA-PSK on the windows side. Tried to join this network in ubuntu, but Network Manager is still not showing a WPA option for me  to enter my psk, only WEP. Am using a netgear WG511 adapter which I read works out of the box with linux. The network manager detects my SSID with a strong signal, but when I select, it gives me a "The requested network requires security capabilities unsupported by your hardware" message. Do I need to install a ndiswrapper?

Thanks for reading.

---

### Post by crispy_420 on 2007-04-26
Did you install wpa-supplicant?

---

### Post by jimmybt on 2007-04-27
Thanks for the reply. That was one of the first things I did, but nothing got installed. I got the message: 'wpasupplicant is already the newest version' which I took to mean its already installed.

---

### Post by jimmybt on 2007-04-27
just check ed in Synaptic. Version 0.5.7-0ubuntu2 installed

---

### Post by hyperair on 2007-05-13
What driver are you using? It can be found in System->Preferences->Hardware Information

---

### Post by hkahwaji on 2007-05-31
I am having the same issue. I can connect to my wireless network when the wireless security is disabled. However, I want to secure the network. 

There is a nice tutorial that explains how to configure WPA-PSK and WPA2 using AES. I will include that.

What I am confused in is the different interfaces. I am connecting to my wireless network via eth1 interface. Shouldn't I connect over wlan0.

My wired connection is over eth0 which makes sense.

Here is the output of ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:17:42:07:AE:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4372502 (4.1 MiB)  TX bytes:690451 (674.2 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:13:02:30:BA:F2  
          inet addr:192.166.1.100  Bcast:192.166.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe30:baf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4733 errors:145 dropped:1207 overruns:0 frame:0
          TX packets:2247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3004777 (2.8 MiB)  TX bytes:240158 (234.5 KiB)
          Interrupt:21 Base address:0xc000 Memory:58100000-58100fff 

eth0:avah Link encap:Ethernet  HWaddr 00:17:42:07:AE:52  
          inet addr:169.254.5.3  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3777 (3.6 KiB)  TX bytes:3777 (3.6 KiB)

Here is the output of iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys-n"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:F8:37:7F:36   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-23 dBm  Noise level=-24 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1065   Missed beacon:0

I verified that the intel 3945 linux driver is loaded using the following command:
dmesg|grep "Intel"

I am not sure why wireless is recognized as ethernet. 

Thanks

---

### Post by hyperair on 2007-05-31
Don't worry about it. eth1 is just a name. Different drivers will create different network interfaces. For example, the acx and ndiswrapper drivers will create the network interface wlan0. However, there's one driver (some Atheros thing or rather, can't remember what it was called) which recognizes the wireless card as ath0. See, it's just a name. Doesn't matter.

---

### Post by AndyPopely on 2007-05-31
I documented this to get my netgear wireless adapter to work ... the bottom line is to stop the linux driver for the adapter being loaded and instead use the windows xp driver for the card wrapped in ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=457581](http://ubuntuforums.org/showthread.php?t=457581)

---

### Post by hyperair on 2007-06-01
EDIT: Sorry, double posted by mistake. I had a power cut morning and thought that the reply didn't get through.

---

