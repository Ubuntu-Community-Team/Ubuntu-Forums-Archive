---
title: "Internet problem"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by pavlick on 2008-02-04
Hello again,

I've had a problem installing Ubuntu using wubi, thank you for the people who helped me with that, but now i've got it up and running. Everything seems to be running just fine, but right now my main problem is the internet. I connect to my wireless network through my Linksys Wireless-G USB adapter, I get a fairly good signal, but the internet just doesn't work. Any help please? thank you

---

### Post by jan quark on 2008-02-04
pls post the results of the terminal commands

```
iwconfig
```

```
ifconfig
```
```

sudo iwlist scan
```

---

### Post by pavlick on 2008-02-04
this is hard since i dont have an internet connection on the computer, so im gonna try to replicate best wat the terminal gives me here.
iwconfig
lo - no wireless extensions

eth0 - no wireless extensions

rausb1 - RT2500USB WLAN ESSID:"linksysk" Nickname: " "
              Mode: managed frequency=2.462 GHz Access Point: oo:oF:66:D7:39:3D
              Bit rate=54 Mb/s
              RTS thr:off Fragment thr:off
              Link quality=72/100 Signal level:-82 dBm Noise level -206 dBm
              Rx invalid nwid:o Rx invalid crypt:0 Rx invalid frag:0
              Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ifconfig (i will only copy out the one for rausb1, i presume thats the wirelss)
rausb1 Link encap:Ethernet HWaddr 00:12:17:9C:40:66
            inet6 addr: fe80::212:17ff:fe9c:4066/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
            RX packets:11 errors:0 dropped:0 overruns:0 frame:0
            TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
           RX bytes:2659064 (2.3 MiB) Tx Bytes:39848 (38.9 KiB)

when i do sudo iwlist scan it asks for a password, when i try to enter anything, nothing feels up the space, so i can get the sudo iwlist scan

---

### Post by Bubba64 on 2008-02-04
Pass words in terminal do not show on screen but just input it then press enter. That is all I can help you with sorry

---

### Post by pavlick on 2008-02-04
sudo iwlist scan

rausb1 scan completed:
cell 01 - address: 00:0F:66:D7:39:3D
Mode:Managed
Essid:"linksysk"
encryption key:off
channel:11

Cell 02 - Address: 00:13:46:A5:4F:A8
mode:managed
essid:"default"
encryption key:on
channel:6

THANK YOU

---

