---
title: "wifi connection but no Internet"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Gribouye on 2008-03-30
Hi Everybody. 

I just migrated my Asus A4000 under Ubuntu 7.10. 
when I click on the network icone in the task bar, I can see my connection among others (my neighboor probably) but once I click on it I cannot use internet.
it seams the drivers for the Wireless works fine but I can't surf the net.
I guess I have to enter my user's name and password somewhere but can't find any password box.

Here some information

> nominoe@nominoe-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:D8:2D:87:8D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2632 (2.5 KB)  TX bytes:2632 (2.5 KB)

nominoe@nominoe-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Under xp, I have the same thing  if I try to connect directly to the ADSL Modem trought the Wlan  (giving the message :Limited or no connectivity) , first I must create a "new connection" using my username and password provide by provider. Is it something like that with Ubuntu?

Thanks for your help, hoping that my english is good enough for you to understand it.

---

### Post by Inxsible on 2008-03-30
Click on the network icon and then select 'Create new wireless network'.Put in your details there like the type of network you have(WPA or WEP ..etc) and then you should be able to connect.

---

### Post by Gribouye on 2008-03-30
Thanks, I've tryed that already. 
It doesn't seams to work.

---

