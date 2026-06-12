---
title: "Network Manager not managing wireless"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Wiggums on 2007-05-04
Everything was working fine.  Then I was trying to connect to a WEP network and I went into network manager and selected "manual configuration".  Now the only options in network manager are wired network and manual configuration.  It will not show any wireless networks.  How do I get network manager back to it's original configuration.

---

### Post by scrooge_74 on 2007-05-04
Is your wireless card working?

type ifconfig in a termilal to see if it is there

If it is there you can type

iwlist eth1(or whatever your systems recognizes as the card) scanning to see if you can pick a wireless network

if the cards is not installed you need to tell which type of card you have.

Also wifi-radar can help you connect to wireless networks

---

### Post by Wiggums on 2007-05-04
I'm pretty sure the wireless is on and working, eth1 is the wireless card and here are the results from iwconfig, iwlist, and ifconfig.  I'm at a hotel using wired connection, the wireless will not connect.  Why does eth1 not have an IP address?

You can see what I am talking about with image I attached.  No wireless options in network manager...

```
graham@frylock:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0B:7D:1D:27:6F  
          inet6 addr: fe80::20b:7dff:fe1d:276f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1891 errors:0 dropped:4112 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108126 (105.5 KiB)  TX bytes:24542 (23.9 KiB)
          Interrupt:10 Base address:0x8000 

graham@frylock:~$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"stayonline"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:0E:D7:48:66:61   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=-33 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

graham@frylock:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:0E:D7:48:66:61
                    ESSID:"stayonline"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=99/100  Signal level=-35 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 24ms ago

graham@frylock:~$ 

```

---

### Post by scrooge_74 on 2007-05-04
good  question, that always gives me problem at hotels and places.

Which version of Ubuntu are you using

Try installing wifi-radar

---

### Post by Wiggums on 2007-05-04
Using 7.04.  Never had a problem at hotel when network-manager was running.  Is there a command I need to type in to the terminal to get an ip address?  What is the same as using "ipconfig /renew"  in windows xp?

---

### Post by scrooge_74 on 2007-05-04
sudo ifdown eth1

then

sudo ifup eth1

---

### Post by Wiggums on 2007-05-04
I installed wfii-radar and am able to use it to configure the wireless.  Network Manager is still not showing any wireless options.

---

### Post by josephus on 2007-05-04
go into network-admin and make sure that the wireless is unchecked.  network-manager will only manage devices not managed by other programs.

---

### Post by luisromangz on 2007-05-04
If you use the "manual configuration" option, then Netowork Manager stops managing the interface, so it doesn't show in the menu.

To make Network Manager manage the wireless interface again, you should remove the info about that interface stored in /etc/network/interfaces.

I hope this helps you.

---

### Post by Wiggums on 2007-05-04
I tried removing the last two lines of that files, but no luck after a reboot.  Here is my /etc/network/interfaces.  What do I need to change?

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface eth1 inet dhcp
wireless-essid atlantic
wireless-key **********
```

---

### Post by scrooge_74 on 2007-05-05
Change the file to this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp

#wireless-essid atlantic
#wireless-key **********

then reboot and let the system find the wireless lan again so you can give the key to it

---

### Post by mastergunner on 2007-08-12
OK I am having the same problem and am a noob at Linux. My system sees the hotel wireless (stayonline) but cannot connect. I am using Kubuntu 7.04. Can someone explain sep by step what I should do to get this working. I appreciate the help guys.





> **scrooge_74 said:**
> Change the file to this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp

#wireless-essid atlantic
#wireless-key **********

then reboot and let the system find the wireless lan again so you can give the key to it

---

### Post by mastergunner on 2007-08-12
Also how do what does wifi-radar do and how do you download it if you cant get online (wireless is only option in hotel)?

---

### Post by mastergunner on 2007-08-13
Anybody?????

---

