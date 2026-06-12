---
title: "Network (eth0) connected, internet won't load"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ewercr on 2007-03-26
Hello all.  I installed ubuntu for the first time on Saturday and had no problem accessing the Internet on both wired and wireless connections at home.  Yesterday, I returned to school and was able to use the local ethernet connection here without a problem.   However, last evening, Firefox refused to load Google, GAIM would not connect, and I was unable to ping yahoo.com, even though my eth0 connection showed that it was connected and receiving packets at a steady rate.  I searched these forums and found a few cases similar to my own, so I tried blacklisting IPv6 and disabling it in Firefox, but it still doesn't work.  Other people suggested DNS issues, but I am not sure how to proceed in that direction. Below, I have copied and pasted the output of ifconfig and iwconfig, since these commands seem to be of some importance.  Your help in this matter is grealty appreciated!

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:D4:33:AD:3B  
          inet addr:129.133.158.244  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: 2002:8185:b406:5:216:d4ff:fe33:ad3b/64 Scope:Global
          inet6 addr: fec0::5:216:d4ff:fe33:ad3b/64 Scope:Site
          inet6 addr: fe80::216:d4ff:fe33:ad3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3679951 (3.5 MiB)  TX bytes:29006 (28.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1552 (1.5 KiB)  TX bytes:1552 (1.5 KiB)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Frequency:nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:54   Missed beacon:0

---

### Post by xueg0i on 2007-03-26
what does "ifconfig eth1 up" say?

---

### Post by ewercr on 2007-03-26
> **xueg0i said:**
> what does "ifconfig eth1 up" say?

eth1: ERROR while getting interface flags: No such device

I have a function button on my laptop which disables the wireless device and I have otherwise disabled the wireless in ubuntu, so I do not believe there is a conflict between my wired and wireless devices.

---

### Post by xueg0i on 2007-03-26
sorry I misread. I thought you were using wireless. Nevertheless, did you try to:
"sudo ifconfig eth0 down"
"sudo ifconfig eth0 up"
"sudo dhclient eth0"
and what is in your /etc/network/interfaces ?

---

### Post by pillu on 2007-03-26
I guess you are using ethernet (wired) connection which is on eth0. Could you try doing this
```
sudo killall dhclient
sudo dhclient eth0
```

and see if it helps ?
cheers
pillu

---

### Post by ewercr on 2007-03-26
> **xueg0i said:**
> sorry I misread. I thought you were using wireless. Nevertheless, did you try to:
"sudo ifconfig eth0 down"
"sudo ifconfig eth0 up"
"sudo dhclient eth0"
and what is in your /etc/network/interfaces ?


> **pillu said:**
> I guess you are using ethernet (wired) connection which is on eth0. Could you try doing this
```
sudo killall dhclient
sudo dhclient eth0
```

and see if it helps ?
cheers
pillu


I tried both of these suggestions, but it still does not work.  Below is my /etc/network/interfaces file

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp













iface eth1 inet dhcp
wireless-essid airwesls



auto eth0

---

### Post by pillu on 2007-03-26
> **ewercr said:**
> I tried both of these suggestions, but it still does not work.  Below is my /etc/network/interfaces file

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp













iface eth1 inet dhcp
wireless-essid airwesls



auto eth0

Some times the other interfaces interfere with the one you want to run. Could you comment out all the other interfaces after eth0. So just put a # mark in front of all the lines from auto eth2 to wireless-essid airwesls...Then restart the network using

sudo ifup eth0

Also my /etc/network/interfaces file has all the auto lines preceding the iface lines. So try moving the auto eth0 line before iface eth0 line.

---

