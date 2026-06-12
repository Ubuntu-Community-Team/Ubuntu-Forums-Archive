---
title: "Wireless active but not working"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by FFfanatic on 2006-11-24
I got my Drake disc yesterday (much thanks to those that sent it) and it's amazing except for one thing. My laptop light is illuminated, meaning that wireless is enabled, but I can't find or connect to any WN, is this just a problem because it's running the LiveCD?

---

### Post by nickburns on 2006-11-24
Go to the terminal and run 'ifconfig' and post back what you get....

---

### Post by FFfanatic on 2006-11-24
ath0      Link encap:Ethernet  HWaddr 00:16:CE:51:AD:B0
          inet addr:130.179.254.73  Bcast:130.179.255.255  Mask:255.255.252.0
          inet6 addr: fe80::216:ceff:fe51:adb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:569 errors:44451 dropped:0 overruns:0 frame:44451
          TX packets:23 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:106149 (103.6 KiB)  TX bytes:2358 (2.3 KiB)
          Interrupt:50 Memory:ffffc200100a0000-ffffc200100b0000

eth0      Link encap:Ethernet  HWaddr 00:16:D4:13:5D:DF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

I also just found something weird. Right now I'm running LiveCD and the internet and all that is working just fine. I guess it could have been that the internet may have been cutting out just at the right time(for it). In relation to this, is there any way to get an icon saying whether my WIFI is connected and how strong the signal is? I checked under the add to panel option but nothing screams out saying "I am your wireless, I am connected and I the signal is XX%!!!!!"

---

### Post by nickburns on 2006-11-26
Go to System >> Administration >> Networking and look for a ath0 (the wireless connection) You should get options to use DHCP, or Static IP and a checkbox to enable the connection.  Once connected you will get a signal strength bar up by the clock.  (Mine is green, and to the left of the Sound Icon)

---

