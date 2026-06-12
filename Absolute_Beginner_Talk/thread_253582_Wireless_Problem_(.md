---
title: "Wireless Problem :("
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by my_cuppa_tea on 2006-09-08
Im having a problem setting up my wireless connection. I have been into Administration -> networking -> wireless and found my connection on the dropdown menu. I have typed in the password and set Eth0 as the default.
Now a red sign has appeared over the connection icon and when I click the message reads:
SIOCGIFFLAGS error: no such device
Im not sure what this means or what to do!:-k 
can anyone help me please??!!! Thanks.

---

### Post by Metacarpal on 2006-09-08
I think Eth0 is your hard-line wired ethernet port.  Do you have an option for wlan0 as the default connection?

---

### Post by my_cuppa_tea on 2006-09-08
ill check that out...thanks

---

### Post by Devile on 2006-09-08
change your eth0 to eth1

---

### Post by jorn on 2006-09-08
What card is it?

---

### Post by my_cuppa_tea on 2006-09-09
ok...
I cant find anything which says wlan0: the only option I seem to get for the default connection is eth0 or eth1.
I tried using eth1 ...but with no joy. It didnt seem to recognise anything and wouldnt let me configure.
I am using an IBM Thinkpad R50e with built in wireless.
If anyone has any more suggestions I would be very grateful :)

---

### Post by jorn on 2006-09-09
Done a search on the net. Should work out of the box.
You say that you wireless card  shows up in >Administration -> networking.
Click on the card. Click on properties, fill out the boxes -  and click ok.
Did you do that?

---

### Post by my_cuppa_tea on 2006-09-09
The same connection that I use on windows shows up. I go into >Administration -> networking -> wireless (eth0)and find the connection no problem. I name the connection Seely, go back to wireless and set eth0 as the default (no other choice) When I set Seely as the connection in the networking icon I get the error message. I checked on the terminal and it does recognise it:

eth0      Scan completed :
          Cell 01 - Address: 00:14:BF:B8:82:55
                    ESSID:"seely"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=70/100  Signal level=-58 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 200ms ago

Its probably something simple that Im doing wrong but I just cant figure it out! Thanks

---

### Post by jorn on 2006-09-09
Will you post your:
> ifconfig -a
To execute in terminal.
Doesn't eth belong to cabled and ra0 to wireless or am I confused?

---

### Post by my_cuppa_tea on 2006-09-10
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:13:CE:96:D6:27
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000 Memory:d0200000-d0200fff

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:C2:8F:C8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:57036 (55.6 KiB)  TX bytes:57036 (55.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

To be honest I have no idea what belongs to what. I think IM in a  little bit over my head now!:confused: 
 I talked to a friend yesterday and he got me to install the network-manager-gnome (and some other files that go along with that). Thought that may fix the problem but Im still getting exactly the same error message (SIOCGIFFLAGS) when i try Administration -> networking -> wireless (eth0) and find my connection. ](*,)

---

### Post by bakert on 2006-09-10
My Thinkpad T43 has the wireless as eth1 but it works fine.  So I wouldn't get hung up trying to change it to wlan0 or anything like that.

---

### Post by my_cuppa_tea on 2006-09-10
ok Ill try again using eth1. I havnt tried that again since I installed network-manager. Thanks.

---

