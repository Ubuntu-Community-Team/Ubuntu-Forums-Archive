---
title: "Firestarter firewall won`t start..."
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by orange2k on 2007-07-04
I installed firestarter, but when I start it, a pop-up shows up saying: "The device eth0 is not ready. Please check your network device settings and make sure your internet connection is active". I have an adsl internet connection and it is working without flaw.

What can I do?

---

### Post by scxtt on 2007-07-04
are you sure you have it assigned to THAT connection and you're not using eth0?  what's the output of **ifconfig**?

---

### Post by orange2k on 2007-07-04
Output:

eth0      Link encap:Ethernet  HWaddr 00:50:BA:6F:66:8E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43106358 (41.1 MiB)  TX bytes:3219692 (3.0 MiB)
          Interrupt:16 Base address:0xd800 

eth0:avah Link encap:Ethernet  HWaddr 00:50:BA:6F:66:8E  
          inet addr:169.254.7.112  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:83.131.68.28  P-t-P:172.29.252.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:31061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:42417311 (40.4 MiB)  TX bytes:2493649 (2.3 MiB)

EDIT: Ive got it: I should have selected ppp0 as my internet connected network device... everything works now!!!

---

### Post by deepclutch on 2007-07-04
for a desktop use,apt-get install **lokkit**  is enough rather than going for gui and dont care much as lokkit(originally for redhat,but u can install from synaptic) is a script that controls iptables as firestarter too does,but carefree that is! :p

---

### Post by orange2k on 2007-07-04
Here is what I got when I tested my connection, first with firestirter turned off, then with firestarter turned on. Not bad, I guess?

---

### Post by kvonb on 2007-07-04
Go through Firestarter's setup again, and select ppp0 as your internet connected device, NOT eth0.

Also set it to restart when the connection goes down/up, because if Firestarter is starting before ppp0 goes up, it will try to use eth0 and complain.

---

### Post by orange2k on 2007-07-04
> **kvonb said:**
> Go through Firestarter's setup again, and select ppp0 as your internet connected device, NOT eth0.

Also set it to restart when the connection goes down/up, because if Firestarter is starting before ppp0 goes up, it will try to use eth0 and complain.

I already did that and it works now. Thanks anyway...

---

