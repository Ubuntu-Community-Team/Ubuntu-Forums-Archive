---
title: "[SOLVED] Cannot scan available networks"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2006-12-08
Hi all,


  I'm not able to scan available networks from command using "iwlist"

  See the code bellow with the 2x results. One right after the other...


```
victor@victor-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:36:9D:2C
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=46/100  Signal level=-76 dBm
                    Extra: Last beacon: 1884ms ago

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

victor@victor-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```


It only gives me my connection information.

Any takes? Thanks...


Vic.

---

### Post by scrooge_74 on 2006-12-08
> **victorbrca said:**
> Hi all,


  I'm not able to scan available networks from command using "iwlist"

  See the code bellow with the 2x results. One right after the other...


```
victor@victor-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:36:9D:2C
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=46/100  Signal level=-76 dBm
                    Extra: Last beacon: 1884ms ago

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

victor@victor-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```


It only gives me my connection information.

Any takes? Thanks...


Vic.

When I scan I use the command iwlist eth1 scanning 

eth1 is my wireless card

hope it helps

---

### Post by victorbrca on 2006-12-08
It ends up giving me the same results

```
victor@victor-laptop:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:36:9D:2C
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=41/100  Signal level=-76 dBm
                    Extra: Last beacon: 3852ms ago
```


Vic.

---

### Post by scrooge_74 on 2006-12-08
sorry i did not read your post well, you have a network there is call linksys some one did not change the name of the router.

---

### Post by victorbrca on 2006-12-08
Found the problem. Apparently you need "sudo" to search for networks.

This will give your interface connection info

```
iwlist scanning
```
or
```
iwlist eth# scanning
```

This will scan for available networks
```
sudo iwlist scanning
```
or
```
sudo iwlist eth# scanning
```

Taurus would be proud of me!!! lol


Vic.

---

### Post by scrooge_74 on 2006-12-08
Still don't know why you need sudo when the results of the scan were there.  It did found a network which should appear also in wifi radar or in the network manager

---

### Post by victorbrca on 2006-12-09
Because that wasn't the complete result. I have about 6 wireless routers on the surroundings...

```
 BSSID              PWR  Beacons   # Data  CH  MB  ENC   ESSID

 03:00:00:00:00:00   -1        0        0   6  -1
 9F:D4:88:00:00:00   -1        0        0   6  -1        &#65533;J&#65533;.&#65533;#&#65533;&#65533;'&#65533;&#65533;%..R3..^F7ab'r.f1..6.
 00:14:BF:00:00:00   -1        5        0   6  48  OPN   linksys
 00:0F:B5:00:00:00   -1        9        0   6  54  WEP?  Mcsystsems
 00:0F:66:00:00:00   -1       26        4   6  48  OPN   linksys
 00:14:BF:00:00:00   -1       29        2   6  48  WPA   Wazem

```


Vic.

---

### Post by houstonbofh on 2006-12-09
> **scrooge_74 said:**
> Still don't know why you need sudo when the results of the scan were there.  It did found a network which should appear also in wifi radar or in the network manager
Because you need direct access to the WiFi card to do this.  That is not a user mode function.

---

