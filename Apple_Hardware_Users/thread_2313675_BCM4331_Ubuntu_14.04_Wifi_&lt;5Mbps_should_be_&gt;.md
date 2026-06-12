---
title: "BCM4331 Ubuntu 14.04 Wifi &lt;5Mbps should be &gt;200"
date: 2016-02-15
forum: Apple Hardware Users
---

### Post by Ken_Kyger on 2016-02-15
Dual booted mac mini and ubuntu, osx getting speeds of over 200Mbps reported by speedtest.net. When the test doesnt timeout on the ubuntu side, I get less than 5Mbps.


Sometimes I cant even get an SSH connection to the box.


Interestingly enough, it also doesnt see any of my 5Ghz networks either.


FutureHax is the network im attempting to connect to.


```
   ########## wireless info START ##########    
    Report from: 15 Feb 2016 00:52 EST -0500
    
    Booted last: 15 Feb 2016 00:44 EST -0500
    
    Script from: 27 Sep 2015 00:34 UTC +0000
    
    ##### release ###########################
    
    Distributor ID:	Ubuntu
    Description:	Ubuntu 14.04.3 LTS
    Release:	14.04
    Codename:	trusty
    
    ##### kernel ############################
    
    Linux 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
    
    \boot\vmlinuz-3.19.0-49-generic.efi.signed, ro, quiet, splash, vt.handoff=7, initrd=boot\initrd.img-3.19.0-49-generic
    
    ##### desktop ###########################
    
    sed: can't read /home/futurehax/.dmrc: No such file or directory
    
    Could not be determined.
    
    ##### lspci #############################
    
    02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    	Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    	Kernel driver in use: tg3
    
    03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    	Subsystem: Apple Inc. AirPort Extreme [106b:00e4]
    	Kernel driver in use: bcma-pci-bridge
    
    ##### lsusb #############################
    
    Bus 002 Device 005: ID 046d:c534 Logitech, Inc. 
    Bus 002 Device 004: ID 0bc2:331a Seagate RSS LLC 
    Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
    Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 004: ID 04e8:61c3 Samsung Electronics Co., Ltd 
    Bus 001 Device 007: ID 05ac:8281 Apple, Inc. 
    Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
    Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    
    ##### PCMCIA card info ##################
    
    ##### rfkill ############################
    
    0: hci0: Bluetooth
    	Soft blocked: no
    	Hard blocked: no
    1: phy0: Wireless LAN
    	Soft blocked: no
    	Hard blocked: no
    
    ##### lsmod #############################
    
    b43                   421888  0 
    mac80211              712704  1 b43
    cfg80211              524288  2 b43,mac80211
    ssb                    65536  1 b43
    bcma                   53248  1 b43
    
    ##### interfaces ########################
    
    auto lo
    iface lo inet loopback
    
    ##### ifconfig ##########################
    
    docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF]>  
              inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
              inet6 addr: fe80::<IP6 'docker0' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:92092 errors:0 dropped:0 overruns:0 frame:0
              TX packets:146569 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:5240274 (5.2 MB)  TX bytes:219047603 (219.0 MB)
    
    eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
              Interrupt:16 
    
    veth256bd9a Link encap:Ethernet  HWaddr <MAC 'veth256bd9a' [IF]>  
              inet6 addr: fe80::<IP6 'veth256bd9a' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:78 errors:0 dropped:0 overruns:0 frame:0
              TX packets:156 errors:0 dropped:1 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:6396 (6.3 KB)  TX bytes:20237 (20.2 KB)
    
    veth6dd5713 Link encap:Ethernet  HWaddr <MAC 'veth6dd5713' [IF]>  
              inet6 addr: fe80::<IP6 'veth6dd5713' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:2110 errors:0 dropped:0 overruns:0 frame:0
              TX packets:2603 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:154972 (154.9 KB)  TX bytes:2673980 (2.6 MB)
    
    veth8c6aa4b Link encap:Ethernet  HWaddr <MAC 'veth8c6aa4b' [IF]>  
              inet6 addr: fe80::<IP6 'veth8c6aa4b' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:8 errors:0 dropped:0 overruns:0 frame:0
              TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:648 (648.0 B)  TX bytes:20935 (20.9 KB)
    
    veth90b9f85 Link encap:Ethernet  HWaddr <MAC 'veth90b9f85' [IF]>  
              inet6 addr: fe80::<IP6 'veth90b9f85' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:8 errors:0 dropped:0 overruns:0 frame:0
              TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:648 (648.0 B)  TX bytes:18783 (18.7 KB)
    
    vetha5d3954 Link encap:Ethernet  HWaddr <MAC 'vetha5d3954' [IF]>  
              inet6 addr: fe80::<IP6 'vetha5d3954' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:8 errors:0 dropped:0 overruns:0 frame:0
              TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:648 (648.0 B)  TX bytes:20755 (20.7 KB)
    
    vethe4d6415 Link encap:Ethernet  HWaddr <MAC 'vethe4d6415' [IF]>  
              inet6 addr: fe80::<IP6 'vethe4d6415' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:89880 errors:0 dropped:0 overruns:0 frame:0
              TX packets:144290 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:6366250 (6.3 MB)  TX bytes:216406793 (216.4 MB)
    
    wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
              inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
              inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:163609 errors:0 dropped:0 overruns:0 frame:0
              TX packets:104454 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:235577751 (235.5 MB)  TX bytes:10873553 (10.8 MB)
    
    ##### iwconfig ##########################
    
    vetha5d3954  no wireless extensions.
    
    eth0      no wireless extensions.
    
    vethe4d6415  no wireless extensions.
    
    docker0   no wireless extensions.
    
    veth256bd9a  no wireless extensions.
    
    veth6dd5713  no wireless extensions.
    
    lo        no wireless extensions.
    
    veth90b9f85  no wireless extensions.
    
    veth8c6aa4b  no wireless extensions.
    
    wlan0     IEEE 802.11bg  ESSID:"FutureHax"  
              Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'FutureHax' [AC5]>   
              Bit Rate=11 Mb/s   Tx-Power=20 dBm   
              Retry short limit:7   RTS thr:off   Fragment thr:off
              Power Management:off
              Link Quality=56/70  Signal level=-54 dBm  
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:519  Invalid misc:444   Missed beacon:0
    
    ##### route #############################
    
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
    172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
    192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
    
    ##### resolv.conf #######################
    
    nameserver 127.0.1.1
    search cfl.rr.com
    
    ##### network managers ##################
    
    Installed:
    
    	NetworkManager
    
    Running:
    
    root      1148     1  0 00:44 ?        00:00:01 NetworkManager
    
    ##### NetworkManager info ###############
    
    NetworkManager Tool
    
    State: connected (global)
    
    - Device: wlan0  [FutureHax] ---------------------------------------------------
      Type:              802.11 WiFi
      Driver:            b43
      State:             connected
      Default:           yes
      HW Address:        <MAC 'wlan0' [IF]>
    
      Capabilities:
        Speed:           11 Mb/s
    
      Wireless Properties
        WEP Encryption:  yes
        WPA Encryption:  yes
        WPA2 Encryption: yes
    
      Wireless Access Points (* = current AP)
        PS4-A9DC9142ED84:Infra, <MAC 'PS4-A9DC9142ED84' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2
        ATT64NqD3u:      Infra, <MAC 'ATT64NqD3u' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2
        You're Too Slow: Infra, <MAC 'You're Too Slow' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
        ATT72493RG:      Infra, <MAC 'ATT72493RG' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
        *FutureHax:      Infra, <MAC 'FutureHax' [AC5]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 66 WPA2
    
      IPv4 Settings:
        Address:         192.168.1.134
        Prefix:          24 (255.255.255.0)
        Gateway:         192.168.1.1
    
        DNS:             192.168.1.1
    
    - Device: eth0 -----------------------------------------------------------------
      Type:              Wired
      Driver:            tg3
      State:             unavailable
      Default:           no
      HW Address:        <MAC 'eth0' [IF]>
    
      Capabilities:
        Carrier Detect:  yes
    
      Wired Properties
        Carrier:         off
    
    ##### NetworkManager.state ##############
    
    [main]
    NetworkingEnabled=true
    WirelessEnabled=true
    WWANEnabled=true
    WimaxEnabled=true
    
    ##### NetworkManager.conf ###############
    
    [main]
    plugins=ifupdown,keyfile,ofono
    dns=dnsmasq
    
    [ifupdown]
    managed=false
    
    ##### NetworkManager profiles ###########
    
    [[/etc/NetworkManager/system-connections/FutureHax_5Ghz]] (600 root)
    [connection] id=FutureHax_5Ghz | type=802-11-wireless
    [802-11-wireless] ssid=FutureHax_5Ghz | mac-address=<MAC 'wlan0' [IF]>
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/FutureHax]] (600 root)
    [connection] id=FutureHax | type=802-11-wireless
    [802-11-wireless] ssid=FutureHax | mac-address=<MAC 'wlan0' [IF]>
    [ipv4] method=auto
    [ipv6] method=auto
    
    ##### iw reg get ########################
    
    Region: America/New_York (based on set time zone)
    
    country 00:
    	(2402 - 2472 @ 40), (3, 20)
    	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    
    ##### iwlist channels ###################
    
    vetha5d3954  no frequency information.
    
    eth0      no frequency information.
    
    vethe4d6415  no frequency information.
    
    docker0   no frequency information.
    
    veth256bd9a  no frequency information.
    
    veth6dd5713  no frequency information.
    
    lo        no frequency information.
    
    veth90b9f85  no frequency information.
    
    veth8c6aa4b  no frequency information.
    
    wlan0     14 channels in total; available frequencies :
              Channel 01 : 2.412 GHz
              Channel 02 : 2.417 GHz
              Channel 03 : 2.422 GHz
              Channel 04 : 2.427 GHz
              Channel 05 : 2.432 GHz
              Channel 06 : 2.437 GHz
              Channel 07 : 2.442 GHz
              Channel 08 : 2.447 GHz
              Channel 09 : 2.452 GHz
              Channel 10 : 2.457 GHz
              Channel 11 : 2.462 GHz
              Channel 12 : 2.467 GHz
              Channel 13 : 2.472 GHz
              Channel 14 : 2.484 GHz
              Current Frequency:2.462 GHz (Channel 11)
    
    ##### iwlist scan #######################
    
    vetha5d3954  Interface doesn't support scanning.
    
    eth0      Interface doesn't support scanning.
    
    vethe4d6415  Interface doesn't support scanning.
    
    docker0   Interface doesn't support scanning.
    
    veth256bd9a  Interface doesn't support scanning.
    
    veth6dd5713  Interface doesn't support scanning.
    
    lo        Interface doesn't support scanning.
    
    veth90b9f85  Interface doesn't support scanning.
    
    veth8c6aa4b  Interface doesn't support scanning.
    
    Channel occupancy:
    
          1   APs on   Frequency:2.412 GHz (Channel 1)
          2   APs on   Frequency:2.437 GHz (Channel 6)
          4   APs on   Frequency:2.462 GHz (Channel 11)
    
    wlan0     Scan completed :
              Cell 01 - Address: <MAC 'ATT64NqD3u' [AC1]>
                        Channel:1
                        Frequency:2.412 GHz (Channel 1)
                        Quality=38/70  Signal level=-72 dBm  
                        Encryption key:on
                        ESSID:"ATT64NqD3u"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                  24 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=000000036f1b228e
                        Extra: Last beacon: 4988ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 02 - Address: <MAC 'PS4-A9DC9142ED84' [AC2]>
                        Channel:6
                        Frequency:2.437 GHz (Channel 6)
                        Quality=44/70  Signal level=-66 dBm  
                        Encryption key:on
                        ESSID:"PS4-A9DC9142ED84"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s
                        Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                        Mode:Master
                        Extra:tsf=00000010836c376b
                        Extra: Last beacon: 2988ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 03 - Address: <MAC '' [AC3]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=49/70  Signal level=-61 dBm  
                        Encryption key:off
                        ESSID:""
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s
                        Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                        Mode:Master
                        Extra:tsf=000000f61d26c205
                        Extra: Last beacon: 128ms ago
              Cell 04 - Address: <MAC '' [AC4]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=51/70  Signal level=-59 dBm  
                        Encryption key:off
                        ESSID:""
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s
                        Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                        Mode:Master
                        Extra:tsf=000000f61d26c97a
                        Extra: Last beacon: 60ms ago
              Cell 05 - Address: <MAC 'FutureHax' [AC5]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=60/70  Signal level=-50 dBm  
                        Encryption key:on
                        ESSID:"FutureHax"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                        Mode:Master
                        Extra:tsf=000000f61d12f1d0
                        Extra: Last beacon: 84ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 06 - Address: <MAC 'ATT72493RG' [AC6]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=42/70  Signal level=-68 dBm  
                        Encryption key:on
                        ESSID:"ATT72493RG"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                  24 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=00000002208570b4
                        Extra: Last beacon: 296ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 07 - Address: <MAC 'You're Too Slow' [AC7]>
                        Channel:6
                        Frequency:2.437 GHz (Channel 6)
                        Quality=27/70  Signal level=-83 dBm  
                        Encryption key:on
                        ESSID:"You're Too Slow"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                                  18 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=0000027d8e1c813b
                        Extra: Last beacon: 3408ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
    
    ##### module infos ######################
    
    [b43]
    filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/b43/b43.ko
    firmware:       b43/ucode9.fw
    firmware:       b43/ucode5.fw
    firmware:       b43/ucode16_mimo.fw
    firmware:       b43/ucode15.fw
    firmware:       b43/ucode14.fw
    firmware:       b43/ucode13.fw
    firmware:       b43/ucode11.fw
    license:        GPL
    author:         Rafa&#322; Mi&#322;ecki
    author:         Gábor Stefanik
    author:         Michael Buesch
    author:         Stefano Brivio
    author:         Martin Langer
    description:    Broadcom B43 wireless driver
    srcversion:     11BDA0A580599B083FE4F2B
    depends:        bcma,ssb,mac80211,cfg80211
    intree:         Y
    vermagic:       3.19.0-49-generic SMP mod_unload modversions 
    signer:         Magrathea: Glacier signing key
    sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
    sig_hashalgo:   sha512
    parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
    parm:           fwpostfix:Postfix for the .fw files to load. (string)
    parm:           hwpctl:Enable hardware-side power control (default off) (int)
    parm:           nohwcrypt:Disable hardware encryption. (int)
    parm:           hwtkip:Enable hardware tkip. (int)
    parm:           qos:Enable QOS support (default on) (int)
    parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
    parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
    parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
    parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)
    
    [mac80211]
    filename:       /lib/modules/3.19.0-49-generic/kernel/net/mac80211/mac80211.ko
    license:        GPL
    description:    IEEE 802.11 subsystem
    srcversion:     1261743510839D352D1D895
    depends:        cfg80211
    intree:         Y
    vermagic:       3.19.0-49-generic SMP mod_unload modversions 
    signer:         Magrathea: Glacier signing key
    sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
    sig_hashalgo:   sha512
    parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
    parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
    parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
    parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
    parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
    parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
    
    [cfg80211]
    filename:       /lib/modules/3.19.0-49-generic/kernel/net/wireless/cfg80211.ko
    description:    wireless configuration support
    license:        GPL
    author:         Johannes Berg
    srcversion:     EF182B558008C23DD85EF03
    depends:        
    intree:         Y
    vermagic:       3.19.0-49-generic SMP mod_unload modversions 
    signer:         Magrathea: Glacier signing key
    sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
    sig_hashalgo:   sha512
    parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
    parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
    
    [ssb]
    filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/ssb/ssb.ko
    license:        GPL
    description:    Sonics Silicon Backplane driver
    srcversion:     551AE4C23939F7FBED9DA61
    depends:        
    intree:         Y
    vermagic:       3.19.0-49-generic SMP mod_unload modversions 
    signer:         Magrathea: Glacier signing key
    sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
    sig_hashalgo:   sha512
    
    [bcma]
    filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/bcma/bcma.ko
    license:        GPL
    description:    Broadcom's specific AMBA driver
    srcversion:     F17244FFF75F9BDF92327ED
    depends:        
    intree:         Y
    vermagic:       3.19.0-49-generic SMP mod_unload modversions 
    signer:         Magrathea: Glacier signing key
    sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
    sig_hashalgo:   sha512
    
    ##### module parameters #################
    
    [b43]
    allhwsupport: 0
    bad_frames_preempt: 0
    btcoex: 1
    hwpctl: 0
    hwtkip: 0
    nohwcrypt: 0
    pio: 0
    qos: 1
    verbose: 2
    
    [mac80211]
    beacon_loss_count: 7
    ieee80211_default_rc_algo: minstrel_ht
    max_nullfunc_tries: 2
    max_probe_tries: 5
    minstrel_vht_only: Y
    probe_wait_ms: 500
    
    [cfg80211]
    cfg80211_disable_40mhz_24ghz: N
    ieee80211_regdom: 00
    
    ##### /etc/modules ######################
    
    lp
    rtc
    
    ##### modprobe options ##################
    
    [/etc/modprobe.d/blacklist-ath_pci.conf]
    blacklist ath_pci
    
    [/etc/modprobe.d/blacklist.conf]
    blacklist evbug
    blacklist usbmouse
    blacklist usbkbd
    blacklist eepro100
    blacklist de4x5
    blacklist eth1394
    blacklist snd_intel8x0m
    blacklist snd_aw2
    blacklist i2c_i801
    blacklist prism54
    blacklist bcm43xx
    blacklist garmin_gps
    blacklist asus_acpi
    blacklist snd_pcsp
    blacklist pcspkr
    blacklist amd76x_edac
    
    [/etc/modprobe.d/blacklist-rare-network.conf]
    alias net-pf-3 off
    alias net-pf-6 off
    alias net-pf-9 off
    alias net-pf-11 off
    alias net-pf-12 off
    alias net-pf-19 off
    alias net-pf-21 off
    alias net-pf-36 off
    
    [/etc/modprobe.d/iwlwifi.conf]
    remove iwlwifi \
    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
    && /sbin/modprobe -r mac80211
    
    [/etc/modprobe.d/mlx4.conf]
    softdep mlx4_core post: mlx4_en
    
    ##### rc.local ##########################
    
    exit 0
    
    ##### pm-utils ##########################
    
    [/etc/pm/config.d/default] (644 root)
    SUSPEND_MODULES="b43 bcma"
    
    ##### udev rules ########################
    
    [/etc/udev/rules.d/70-persistent-net.rules]
    # PCI device 0x14e4:0x16b4 (tg3)
    SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
    # PCI device 0x14e4:0x4331 (b43)
    SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
   
    ########## wireless info END ############
```

---

