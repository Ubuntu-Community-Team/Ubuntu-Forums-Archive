---
title: "wireless problems w/ gutsy"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-11-25
i just upgraded to gutsy and i am now having connection problems with my wireless.  I have to go to a terminal window every time i boot up my laptop to be able to use the internet.  I didn't have this problem with edgy or feisty.  It is as if the network manager doesn't remember my WEP key or to run dhclient.  Once I go through the steps that you see below I can successfully connect to the web.  However I have to do this every time I boot up.  Here is the output from my terminal window maybe that can help one of you guys or gals to figure out what to do to correct my problem.  P.S.  I am using gnome not KDE.

brad@brad-laptop:~$ sudo su
[sudo] password for brad:
root@brad-laptop:/home/brad# wlanconfig ath0 list scan
SSID            BSSID              CHAN RATE  S:N   INT CAPS
Dalcourt        00:90:4c:7e:00:6e   11   54M 24:0   100 EPs  WPA
TheRabbitsHole  00:18:4d:83:80:06   11   54M 45:0   100 EPSs
0x000000000...  00:09:5b:e7:74:2e   11   54M 15:0   100 EPSs ATH
at&t            00:0d:14:01:0a:81    6   54M  6:0   100 ESs 
root@brad-laptop:/home/brad# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"TheRabbitsHole"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:83:80:06   
          Bit Rate:54 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3841-3236-3744-3637-3839   Security mode:restricted
          Power Management:off
          Link Quality=45/70  Signal level=-51 dBm  Noise level=-96 dBm
          Rx invalid nwid:5733  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@brad-laptop:/home/brad# iwconfig ath0 essid TheRabbitsHole
root@brad-laptop:/home/brad# iwconfig ath0 key 8A267D6789
root@brad-laptop:/home/brad# dhclient ath0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:e3:df:d5:af
Sending on   LPF/ath0/00:16:e3:df:d5:af
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 10.0.0.1
bound to 10.0.0.4 -- renewal in 951436991 seconds.
root@brad-laptop:/home/brad# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"TheRabbitsHole"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:83:80:06   
          Bit Rate:54 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:8A26-7D67-89   Security mode:restricted
          Power Management:off
          Link Quality=45/70  Signal level=-51 dBm  Noise level=-96 dBm
          Rx invalid nwid:8509  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@brad-laptop:/home/brad#

---

### Post by elctb on 2007-11-25
To get the interface to automatically come up after booting up you need to add the "auto" keyword to the interface in the /etc/network/interfaces file. This is what my /etc/network/interfaces file looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

I believe you need a wpa_supplicant.conf file to get the wep key configured automatically. Take a look at "man wpa_passphrase" and "man wpa_supplicant.conf".

---

### Post by bradmayne on 2007-11-28
this is what i have.  Shouldn't eth1 be ath0? 

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid TheRabbitsHole
wireless-key 8A267D6789

auto eth2
#iface eth2 inet dhcp


auto wlan0
#iface wlan0 inet dhcp

---

### Post by xeth_delta on 2007-11-28
Please post the output for **ifconfig** and **iwconfig**. Don't forget to place the output between code statemets to make reading them easier.

Xeth

---

### Post by Threbus5 on 2007-11-29
I had a similar problem.

Because eth0 and wlan0 were both set to "auto" they either conflicted or sometimes upon boot eth0 became the network default and wlan0 would not connect. The inconsistency was  frustrating.

My solution consisted of removing "auto" from eth0 in the network interfaces file.

Good luck

---

### Post by darrenleeweber on 2007-11-30
I have a Lenovo ThinkPad T61 running Gutsy amd64.  I have a fairly reliable network connection using no setting in /etc/network/interfaces, ie:

root@skiweber:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

All the network connections are managed by the network-manager.  For most of the time, it handles the eth0 and wlan0 connections very well.  It stores the default ESSID and WEP key across boot sessions.  I do have a problem with the wireless connection dropping out when using update manager.  Every time it gets a load of downloads, it gets a little way into the process and fails.  This hangs both the laptop connectivity and the wireless router.  Everything needs to be rebooted.

The only insight I can find so far is that every time it fails I see the following in /var/log/kern.log:

kernel: wlan0: CTS protection disabled (BSSID=00:09:5b:85:4a:bc)

As soon as this happens, the connection fails and hangs everything.  Any help with this would be great.  I may have to start a more specific thread on this issue.

---

### Post by Raptor45 on 2007-12-11
I have been experiencing the very same issue. I haven't been able to discover a solution, have you had any luck?

> **darrenleeweber said:**
> I have a Lenovo ThinkPad T61 running Gutsy amd64.  I have a fairly reliable network connection using no setting in /etc/network/interfaces, ie:

root@skiweber:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

All the network connections are managed by the network-manager.  For most of the time, it handles the eth0 and wlan0 connections very well.  It stores the default ESSID and WEP key across boot sessions.  I do have a problem with the wireless connection dropping out when using update manager.  Every time it gets a load of downloads, it gets a little way into the process and fails.  This hangs both the laptop connectivity and the wireless router.  Everything needs to be rebooted.

The only insight I can find so far is that every time it fails I see the following in /var/log/kern.log:

kernel: wlan0: CTS protection disabled (BSSID=00:09:5b:85:4a:bc)

As soon as this happens, the connection fails and hangs everything.  Any help with this would be great.  I may have to start a more specific thread on this issue.

---

