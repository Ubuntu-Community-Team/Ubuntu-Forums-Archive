---
title: "Network Manager Help"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by NavmaN on 2006-11-13
Hi,
recently, I installed network manager, but it only added one new icon, and the only option is list when I click it is wired network. It doesn't detect a wireless network even though I'm connected to one. My card is even supported it's intel ipw2100.

Thanks,

also, are there any alternatives to network manager that make connected to wlans similar to windows?

---

### Post by BlaY0 on 2006-11-14
What does iwconfig say?

What doest dmesg|grep ipw2200 say?

---

### Post by NavmaN on 2006-11-14
This is what iwconfig says, note: this is what it sais while I am connected to my desired access point:```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"divan21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:71:B4:8E
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-51 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

this is what the other command says, note again, this is while I'm connected to my desired wlan.

```
 dmesg|grep ipw2200
[17179585.264000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1[17179585.264000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179585.264000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179586.024000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[17179586.280000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
 
```

---

### Post by akniss on 2006-11-14
You need to comment out all the lines in /etc/network/interfaces except those containing lo so that it looks something like this:

```
sudo gedit /etc/network/interfaces
```

```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#iface eth1 inet dhcp

```

network-manager won't manage devices with settings there.

---

