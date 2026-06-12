---
title: "can't crack my wep key with my 10.04 macbook 5,1."
date: 2010-10-30
forum: Apple Hardware Users
---

### Post by bl42ed0 on 2010-10-30
```
laptop:~$ sudo /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:5.32 GHz  Access Point: 00:1C:10:A8:A2:53   
          Bit Rate=11 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Encryption key:eek:ff
          Power Managementmode:All packets received
          Link Quality=1/5  Signal level=-80 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:270  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
laptop:~$ sudo airodump-ng wlan0
Interface wlan0: 
ioctl(SIOCGIFINDEX) failed: No such device
-laptop:~$ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.
laptop:~$ sudo airmon-ng start eth1


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
828    avahi-daemon
829    avahi-daemon
839    NetworkManager
936    wpa_supplicant
2629    dhclient
Process with PID 2629 (dhclient) is running on interface eth1


Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

```

so i have been trying to figure this out for the last couple of days and i dunno what i am doing wrong. i have aircrack installed but when i run /sbin/iwconfig it tells me i have no wireless device, however i am connected to a weak wireless signal right now as i am typing this(which is also why i have not bothered to search for an answer in the forums because the signal is so damn slow...sorry)

---

### Post by v1ad on 2010-10-30
hmm if i remember correctly not all wireless devices support aircrack. 

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)

---

### Post by bl42ed0 on 2010-10-31
great..can i find out the wep key without aircrack? is there another program to use??

---

