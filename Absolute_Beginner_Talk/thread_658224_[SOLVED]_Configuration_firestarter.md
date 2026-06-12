---
title: "[SOLVED] Configuration firestarter ???"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Gipsy25 on 2008-01-04
Hello there, well i installed firestarte on my pc (ubunutu 7.10) and everything went fine ... 
my problem is that i cant make it to work with my wireles card 
It shows :DETECTED DEVICE : UNKNOWN DEVICE (wifi0)

Is there a way to change some settings and have the firewall to recognize the wifi card ? 

thanks in advance
 (i am new at ubuntu i had a lot of trouble installing the wifi ... finally i got it to work (felt good) now i wish i can fix this issue too.)

---

### Post by p_quarles on 2008-01-04
Did you get the device name correct? Run
```
ifconfig -a
```
to get a list of your known network devices and their device names.

---

### Post by Gipsy25 on 2008-01-04
This is what i get when i do ifconfig - a 

**********************************

ath0      Link encap:Ethernet  HWaddr 00:18:E7:28:3F:BC  
          inet addr:192.168.0.65  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe28:3fbc/64 Scope:Link
          RX packets:12944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9115838 (8.6 MB)  TX bytes:1505096 (1.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:07:6C:B5  
          
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xd400 

eth1      Link encap:Ethernet  HWaddr 00:80:AD:C8:1F:87  
          inet6 addr: fe80::280:adff:fec8:1f87/64 Scope:Link
          
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:8 dropped:0 overruns:0 carrier:16
          collisions:136 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1152 (1.1 KB)
          Interrupt:20 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48734 errors:0 dropped:0 overruns:0 frame:248
          TX packets:9940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:12484560 (11.9 MB)  TX bytes:1809044 (1.7 MB)
          Interrupt:21 

*********************************************
I noticed that if i change it to eth0 (also unknown device) i can start the the firewall and every time i use the browser i will show activity. 
So i dont know what im doing wrong and why i cant use wifi0 instead of eth0.
I also have 3 nic cards on my computer one is onboard the other one is an internal pci nic and the wifi 
*****************************************

---

### Post by seventhc on 2008-01-04
You probably need to set the device to  ath0
then it should work.
after you open firestarter, click on preferences, then network settings then after you change it, click accept.

---

### Post by p_quarles on 2008-01-04
Hmm. wifi0 certainly seems to be working, given the transmission statistics, but it's saying the device type is "unspecified." 

You can try seventhc's suggestion of changing the device name, but I'm not 100% sure that Firestarter alone will allow you to do that. Only one way to find out, though. ;)

If that doesn't work, though, we can try setting a simple iptables rule (Firestarter is a front-end for iptables) on wifi0, and see if you get a different result.

---

### Post by Gipsy25 on 2008-01-04
It works if i change it to ath0 i mena that is the only way i have to connect to the internet using wifi, and i was checking the activity and every time i browse something it shows the ports and all that but only under ath0. but its working now.
Now i would like to know if i can set the firewall to work with wifi0...

Thanks

---

### Post by seventhc on 2008-01-04
If it's working, why would you want to change it?? ath0 is the device showing your internal ip etc, so it is set up correctly...correct me if I'm wrong though.

---

### Post by Gipsy25 on 2008-01-04
no you are right ... no problem so i will leave it as it is ..you are right ...

thanks ...

---

### Post by p_quarles on 2008-01-04
> **seventhc said:**
> If it's working, why would you want to change it?? ath0 is the device showing your internal ip etc, so it is set up correctly...correct me if I'm wrong though.
Agreed. The only thing I would do is make sure that it is correctly set up as the active interface. You can do that by running:
```
netstat -iv
```
Post the output if you need help interpreting it.

---

