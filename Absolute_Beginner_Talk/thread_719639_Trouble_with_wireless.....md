---
title: "Trouble with wireless...."
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by patree on 2008-03-09
My problem is that for some reason when i click on the wireless i do not have the option to choose a network, there is no list of wireless options. i am sure that my card is supported because ive used this same computer for wireless on ubuntu before (i tried out fedora and decided to come back) but now i have this strange problem. My restricted drivers are Enabled. 
Any help would be appreciated!

---

### Post by patree on 2008-03-09
heres a pic of what i see

---

### Post by jan quark on 2008-03-09
can you please post the results of these terminal commands

```
iwconfig
```

```
sudo iwlist scan
```

```
cat /etc/network/interfaces
```

---

### Post by prshah on 2008-03-09
If I were you, I'd simply click on "Connect to other wireless network..."

Cheers,
PRShah

---

### Post by patree on 2008-03-09
patree@patree-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


patree@patree-laptop:~$ sudo iwlist scan
[sudo] password for patree: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


patree@patree-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

