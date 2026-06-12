---
title: "can't save network settings"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2007-12-26
Hi all,

I am using Ubuntu 7.10 and am using a Belkin wireless router for a local network at home. Everytime I boot up, I have to go to the System -> Network -> Connections -> Properties and give the WEP key to get the wireless to work. How can I save the settings and get it to work automatically upon booting?

Here are some details. The output for "iwconfig" is:

[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"kafka"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:A2:35:A2   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/100  Signal level=-72 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:939   Missed beacon:0

[/HTML]

Here is the output of "sudo cat /etc/network/interfaces"

[HTML]auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-key xxxxxxxx
wireless-essid xxxxxxx

auto eth1
[/HTML]

I have removed the true names of the wireless-key and the wireless-essid and replaced them by a bunch of xxxxx.

Any suggestions on saving the network settings. (I have tried saving it with a name for a location in the network manager, but that does not seem to work). 

Aam-aadmi

---

### Post by ubutufan on 2007-12-26
Try this

auto lo
iface lo inet loopback


#iface eth1 inet dhcp
#wireless-key xxxxxxxx
#wireless-essid xxxxxxx

#auto eth1

---

### Post by aam-aadmi on 2007-12-28
That doesn't work.

---

