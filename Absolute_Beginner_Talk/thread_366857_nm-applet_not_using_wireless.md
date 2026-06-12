---
title: "nm-applet not using wireless"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-02-21
I use nm-applet along with network-manager-gnome

I can get a wired connection no problem, but when I first installed it nm-applet would automatically try and grab a wireless network.

Now nm-applet does not even give me the chance to use wireless?

my iwconfig is here:
charles@charles-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"tcmamed"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:FC:BF:0A
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-30 dBm  Noise level=-31 dBm
          Rx invalid nwid:0  Rx invalid crypt:48  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

[1]+  Terminated              nm-applet

I want to be able to connect to the tcmamed access point, before the little applet would display a drop down of all available wireless networks but now it only shows my wired connection???

Any help would be greatly appreciated.

Chuck

---

### Post by jpeddicord on 2007-02-21
To fix this, open your interfaces file in gedit (`sudo gedit /etc/network/interfaces` in the terminal) and comment out every line but the first two labeled "auto lo" and "loopback". To comment out a line, just add a # in front of it. For example, here is my interfaces file:```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

```Do **not** use this file however, as our systems are probably very different and this file might break your wireless completely.

Jacob

---

### Post by charles.g.moore on 2007-02-22
JacobMP,

Thanks!!! Your instructions worked perfectly!!!
You don't know how happy I am to have my wireless back :-)

Situation Resolved...

---

