---
title: "Setting up Wireless"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by jopv on 2007-05-11
I've installed Feisty Fawn but don't have the wireless automatically setup.

Is there any documentation on how to set it up?

---

### Post by wormser on 2007-05-11
First you want to find out what wireless card and chipset you have.

```
lspci
```

Post the results.

---

### Post by astrosoup on 2007-05-11
I am having a similar problem. I am working on a Compaq with a dreaded Broadcom 43xx card. I had the card working to the point where WiFi Radar would recognize it, updated to Feisty Fawn and fiddled with it to get it recognized again. But as far as I can tell, Wi-Fi radar should have some sort of "connect" button or something, and it doesn't. It finds my network as well as several neighboring ones, but it never connects to anything. Creating an additional connection does not help me either. The "Edit" "Delete" and "Disconnect" buttons warrant no response. I'm brad new to Linux, so I'm not sure where to go from here.

---

### Post by ghostboy on 2007-05-11
> **astrosoup said:**
> I am having a similar problem. I am working on a Compaq with a dreaded Broadcom 43xx card. I had the card working to the point where WiFi Radar would recognize it, updated to Feisty Fawn and fiddled with it to get it recognized again. But as far as I can tell, Wi-Fi radar should have some sort of "connect" button or something, and it doesn't. It finds my network as well as several neighboring ones, but it never connects to anything. Creating an additional connection does not help me either. The "Edit" "Delete" and "Disconnect" buttons warrant no response. I'm brad new to Linux, so I'm not sure where to go from here.

Check out this post [http://ubuntuforums.org/showthread.p...light=broadcom](http://ubuntuforums.org/showthread.p...light=broadcom) if you follow the directions step by step, you should be fine. However depending on the model of your wireless card this may not work, if that is the case, look here [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102). I found this to be a really great resource. I hope this helps.

---

### Post by NICU on 2007-05-11
Using Feisty my wifi card was automatically detected and worked.  However connecting to your network may require some configuring.  At home I don't use encryption on my wireless network (just MAC filters - yes its unsafe).  Anyway, I can usually get my network up and running by typing:
```
sudo ifdown eth0
sudo iwconfig eth0 essid MY_SSID
sudo ifup eth0
```
If that doesn't help please post some more info - what type of Broadcom chipset are you using?  Are there any other details about your wireless network like WEP, MAC filters, anything else? -Good luck

---

### Post by astrosoup on 2007-05-11
Okay

Ghostboy- For some reason, your first link didn't work... it just sent me back to the forum's homepage. The second one looks like instructions to set up ndiswrapper, which I am pretty sure I've done. I recognize the thread as one that I've been through in my trying to fix this.

NICU- I tried your trick and got tripped up on your second step. With my ssid replacing yours, I got this error: 

 SET failed on device eth0 ; Invalid argument.

Remember, My wireless card (BCM4306) is recognized by Feisty Fawn. I've tried joining several 
networks, but there is no way for me to get wi-fi radar to connect to any of them. Their is no "connect" button or anything. Network manager doesn't connect me either. For the sake of experiment I am trying mostly on a unsecured 802.11g network (managed).

And, thanks for the help.

---

### Post by jopv on 2007-05-13
I still don't have connection

I have an Intel chipset 915GM

Details on my wireless network include WEP encryption and MAC filters

I really need help on this

---

### Post by jopv on 2007-05-14
I haven't got anywhere with the connection but here are the details (below) after I typed ifconfig.  I assume 'ath0' is my wireless connection, right?  How do I connect to my router?

varghese2go@varghese2go-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:19:7D:D9:91:F2  
          inet6 addr: fe80::219:7dff:fed9:91f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:36:25:37:87  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe25:3787/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128085 (125.0 KiB)  TX bytes:15002 (14.6 KiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-D9-91-F2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:354
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:9972 (9.7 KiB)  TX bytes:4600 (4.4 KiB)
          Interrupt:23

---

### Post by apienk01 on 2007-05-14
It is strange, because your eth0 and ath0 are "RUNNING" simultaneously. Try this, provided you have set up DHCP on your AP, and you don't use WPA encryption:

```

sudo ifdown eth0
sudo ifdown ath0
sudo iwconfig ath0 essid YOUR_SSID
sudo ifup ath0

```

If you cannot connect this way, please provide the output from:

```
iwconfig
```

---

### Post by jopv on 2007-05-14
I finally got the wireless to work.  I was trying to connect using DHCP automatically.  I changed to Static IP address and it worked.  I'm now officially "wirelessly" online :-)

As a non-techie person it feels good to have solved it on my own rather than taking it to an expert.  The experts are all online ;-) - Thanks for the support.

---

