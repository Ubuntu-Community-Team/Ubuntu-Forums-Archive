---
title: "No Wireless Connection"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by molcanic on 2006-10-11
Having an issue with my wireless connection,completely new to the Linux OS.
I have poked around a bit but need some really basic help.It seems Lan is working but not my Wlan is not.Poked around abit in terminal and found this intersting.Where can i go from here to get my Wlan functioning.All help is much apperciated.


0000:06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)

0000:06:02.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0 01a (rev 01)

---

### Post by davmac on 2006-10-12
There's a thread about getting an RTL8139 wireless working at [http://www.ubuntuforums.org/showthread.php?t=206185&highlight=rtl8139](http://www.ubuntuforums.org/showthread.php?t=206185&highlight=rtl8139)

Hope this helps,

Dave Mac

---

### Post by glenduncanscott on 2006-10-12
You might want to follow this guide [here]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29").

Off the top of my head if you install ndiswrapper package by searching in System>Administration>Synaptic Package Manager

Use: 

```
sudo ndiswrapper -i yourfile.inf
``` 

to install the appropriate window driver.

Then open System>Administration>Networking
Enter ESSID (Network Name), WEP Key etc. 

Make sure wireless hardware switch is on, then reboot. Should work a treat ;)

---

### Post by molcanic on 2006-10-12
Installed the ndiswrapper package.But still no wireless connection.My lan is working but i cant seem to get my wireless to work(its a laptop).Did an iwconfig command and still came up with the same:



lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

