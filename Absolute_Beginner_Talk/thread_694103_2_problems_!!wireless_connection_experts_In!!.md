---
title: "2 problems !!wireless connection experts In!!"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by pinkkiss110 on 2008-02-11
1. My wireless connection can't [COLOR="Red"]_**remember its password**_[/COLOR]. (pops up everytime in startup.)
I know when I was using live CD a thing pops up and requests for a password to remember, but it doesn't happen after I install it.

2. Bad bad connections. *_[COLOR="Red"]Drops every 10 minutes[/COLOR]_* and very hard to reconnect!
Any idea??

ps.I appreciate any help at all! And if there is any files you guys need, tell me! 

Thanks.
[COLOR="Indigo"]================================================[/COLOR]

_[COLOR="Red"]lspci[/COLOR]_
> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem

_[COLOR="Red"]sudo lshw -C network[/COLOR]_
>   *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:10:6c:df:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g


[COLOR="Red"]_iwconfig_[/COLOR]
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"XiaoWang"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:3B:FD:E0   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"XiaoWang"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:3B:FD:E0   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[COLOR="Red"]_susudo iwlist scan_[/COLOR]
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:3B:FD:E0
                    ESSID:"XiaoWang"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-64 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000b91d804c7c


ps. Sorry for the slow reply

---

### Post by jan quark on 2008-02-11
run this in terminal and post the output please

```
lspci
```
```

sudo lshw -C network
```
```

iwconfig
```

```
sudo iwlist scan
```

---

### Post by jw5801 on 2008-02-11
> **pinkkiss110 said:**
> 1. My wireless connection can't [COLOR="Red"]_**remember its password**_[/COLOR]. (pops up everytime in startup.)
I know when I was using live CD a thing pops up and requests for a password to remember, but it doesn't happen after I install it.
That's nm-applet for ya! You can try [this](http://ubuntuforums.org/showthread.php?t=187874) thread to patch it, or you could try using a different network manager. wifi-radar is the first one that springs to mind, there're a few though. All available in the repositories.

> 2. Bad bad connections. *_[COLOR="Red"]Drops every 10 minutes[/COLOR]_* and very hard to reconnect!
Any idea??

ps.I appreciate any help at all! And if there is any files you guys need, tell me! 

Thanks.

Post some hardware/configuration information as requested above and we'll see!

---

