---
title: "Extrange wireless problem"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by lavi on 2007-09-03
Hi all.

I Have just installed ubunty feisty, everything worked fine, but since 1 week ago, i'm unable to stablish a connection with an open wireless.

On my Xp I have no problems connecting with the same SSID. 
Also, the wireless list that appear on the upper right corner, only 1 of the SSID availables appears with an orange bar (something more than the half of the bar).

I don't recall having installed anything  uncommon,
Which could be the problem?

BTW, my card is an Conceptronic RT61 (at least is listed as rt61 in linux).

Sorry for my lousy english...

---

### Post by jw5801 on 2007-09-03
If you put ```
sudo iwlist scan
```into a terminal what is the output?

Lets also have a look at ```
ifconfig
iwconfig
```

---

### Post by lavi on 2007-09-04
That is what I get when running those commands.
Please note that when using windows I have no problems connecting with SSID 3Com or Wireless

```
lavi@ryu:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
eth1      Interface doesn't support scanning. 
 
ra1       Scan completed : 
          Cell 01 - Address: 00:16:38:C4:B6:00 
                    ESSID:"Jazztel Wireless" 
                    Mode:Managed 
                    Channel:11 
                    Encryption key:off 
                    Quality:52/100  Signal level:-73 dBm  Noise level:-256 dBm 
          Cell 02 - Address: 00:60:B3:EC:2A:C2 
                    ESSID:"WLAN_3C" 
                    Mode:Managed 
                    Channel:1 
                    Encryption key:on 
                    Quality:0/100  Signal level:-69 dBm  Noise level:-256 dBm 
          Cell 03 - Address: 00:16:CE:7F:55:80 
                    ESSID:"WANADOO-EFB8" 
                    Mode:Managed 
                    Channel:1 
                    Encryption key:on 
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm 
          Cell 04 - Address: 00:60:B3:51:92:92 
                    ESSID:"WLAN_F1" 
                    Mode:Managed 
                    Channel:1 
                    Encryption key:on 
                    Quality:0/100  Signal level:-71 dBm  Noise level:-256 dBm 
          Cell 05 - Address: 00:16:38:CC:1A:CE 
                    ESSID:"WLAN_4A" 
                    Mode:Managed 
                    Channel:3 
                    Encryption key:on 
                    Quality:0/100  Signal level:-71 dBm  Noise level:-256 dBm 
          Cell 06 - Address: 00:01:38:3C:FD:2B 
                    ESSID:"WLAN_KEOPS" 
                    Mode:Managed 
                    Channel:6 
                    Encryption key:on 
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm 
          Cell 07 - Address: 00:60:B3:F2:5E:6C 
                    ESSID:"WLAN_9F" 
                    Mode:Managed 
                    Channel:7 
                    Encryption key:on 
                    Quality:0/100  Signal level:-71 dBm  Noise level:-256 dBm 
          Cell 08 - Address: 00:13:49:9D:C9:30 
                    ESSID:"WLAN_34" 
                    Mode:Managed 
                    Channel:8 
                    Encryption key:on 
                    Quality:0/100  Signal level:-77 dBm  Noise level:-256 dBm 
          Cell 09 - Address: 00:01:38:8F:99:DA 
                    ESSID:"WLAN_9B" 
                    Mode:Managed 
                    Channel:8 
                    Encryption key:on 
                    Quality:0/100  Signal level:-77 dBm  Noise level:-256 dBm 
          Cell 10 - Address: 00:60:B3:F4:28:CB 
                    ESSID:"WLAN_72" 
                    Mode:Managed 
                    Channel:9 
                    Encryption key:on 
                    Quality:0/100  Signal level:-65 dBm  Noise level:-256 dBm 
          Cell 11 - Address: 00:02:CF:4D:C0:3C 
                    ESSID:"WLAN_90" 
                    Mode:Managed 
                    Channel:9 
                    Encryption key:on 
                    Quality:0/100  Signal level:-65 dBm  Noise level:-256 dBm 
          Cell 12 - Address: 00:13:49:9E:0E:62 
                    ESSID:"WLAN_9E" 
                    Mode:Managed 
                    Channel:9 
                    Encryption key:on 
                    Quality:0/100  Signal level:-69 dBm  Noise level:-256 dBm 
          Cell 13 - Address: 00:13:49:A6:BE:E0 
                    ESSID:"WLAN_D6" 
                    Mode:Managed 
                    Channel:10 
                    Encryption key:on 
                    Quality:0/100  Signal level:-75 dBm  Noise level:-256 dBm 
          Cell 14 - Address: 00:03:C9:8D:01:0B 
                    ESSID:"jjjjj" 
                    Mode:Managed


```

---

