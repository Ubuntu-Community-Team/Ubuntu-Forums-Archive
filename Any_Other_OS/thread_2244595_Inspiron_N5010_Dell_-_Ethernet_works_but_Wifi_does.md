---
title: "Inspiron N5010 Dell - Ethernet works but Wifi doesn't"
date: 2014-09-17
forum: Any Other OS
---

### Post by dj_shab on 2014-09-17
Hi guys I recently installed Zorin 9 (yes I know this isn't the right forum for it, but their forum doesn't seem to add me for some reason) and read that Zorin was Ubuntu based. I was wondering if anyone can please help me setup up my wireless device. I am running a partition of win 7 and Zorin 9 thank you so much.

---

### Post by praseodym on 2014-09-17
Please show the terminal outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by dj_shab on 2014-09-18
uname -a


Linux username 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux




lspci -nnk | grep -iA2 net


12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0447]
    Kernel driver in use: r8169




lsusb


Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




lsmod


Module                  Size  Used by
btrfs                 835954  0 
xor                    21411  1 btrfs
raid6_pq               97812  1 btrfs
libcrc32c              12644  1 btrfs
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
i915                  783805  4 
i2c_algo_bit           13413  1 i915
drm_kms_helper         53081  1 i915
drm                   303102  5 i915,drm_kms_helper
psmouse               106678  0 
ahci                   25819  2 
r8169                  67581  0 
libahci                32716  1 ahci
mii                    13934  1 r8169
wmi                    19177  0 
video                  19476  1 i915




iwconfig


eth0      no wireless extensions.


lo        no wireless extensions.




rfkill list


this one did nothing

---

### Post by Bucky Ball on 2014-09-18
*Thread moved to **Other Operating Systems and Projects**.*

Welcome. No, it's not the forum for it. Fine in this section, though. Good luck.

---

### Post by praseodym on 2014-09-18
Install the missing firmware via:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by dj_shab on 2014-09-18
Rebooting now

---

### Post by dj_shab on 2014-09-18
1 thing to add i did run these commands earlier today after posting 

sudo apt-get update
sudo apt-get dist-upgrade

the last one took a while to install and it brought the wifi up but it won't connect to it.

---

### Post by praseodym on 2014-09-18
Please show those outputs again, plus
```

sudo iwlist scan
iwlist chan
dmesg | grep brcm
```

---

### Post by dj_shab on 2014-09-18
sudo iwlist scan


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 30:46:9A:58:24:52
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Puzzle1001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000250b0a626b9
                    Extra: Last beacon: 188ms ago
                    IE: Unknown: 000A50757A7A6C6531303031
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD860050F204104A000110104400010210570001011041000100103B0001031047001094F06F2DDB081F7C0AAC4917FF4CF3491021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084103C000101
                    IE: Unknown: DD090010180207F0010000
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 02 - Address: 60:C3:97:45:24:39
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"STEFFEN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002efcfac58bd
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00075354454646454E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 03 - Address: B8:E6:25:6C:D4:39
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"2WIRE849"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004a960718181
                    Extra: Last beacon: 652ms ago
                    IE: Unknown: 00083257495245383439
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 94:C1:50:3A:09:59
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"2WIRE546"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a74f3933be
                    Extra: Last beacon: 444ms ago
                    IE: Unknown: 00083257495245353436
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 05 - Address: 30:85:A9:6A:4C:8C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"AFlinksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000bb7c70cce02
                    Extra: Last beacon: 776ms ago
                    IE: Unknown: 000941466C696E6B737973
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503001D127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD8F0050F204104A0001101044000102103B00010310470010BC329E001DD811B286013085A96A4C8C102100154153555354654B20436F6D707574657220496E632E1023000A57505320526F757465721024000752542D4E3536551042000830303030303030301054000800060050F20400011011000F415355532057505320526F7574657210080002210C103C000101
          Cell 06 - Address: 20:AA:4B:85:C3:56
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Taci"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c9436442f9
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000454616369
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD910050F204104A0001101044000102103B000103104700103FC47673D9FF8DE9FC9BFC9068662A7710210013436973636F2053797374656D732C20496E632E1023000E4C696E6B737973204541323730301024000645413237303010420001311054000800060050F20400011011000D436973636F3539313738204150100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180203F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 20:AA:4B:1B:5F:98
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"keswick"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000787f08a199
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 00076B65737769636B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180203F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




iwlist chan




eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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






dmesg | grep brcm




[   22.992336] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   22.997993] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   31.146822] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   31.146834] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  104.757477] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  104.757481] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  111.589694] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  111.589708] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  117.010649] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  117.010654] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  123.610982] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  123.610993] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)

---

### Post by praseodym on 2014-09-18
Which of these network cells is yours? Try

1) a fixed channel
2) pure WPA2-AES (CCMP) encryption
3) bandwidth 20 MHz instead of 20/40MHz
4) MAC address filter off
5) router firmware is up to date?

All these settings can be adjusted in your router interface. Check the manual

---

### Post by dj_shab on 2014-09-18
read a few things on the site today and ran these in the terminal 

sudo apt-get update
sudo apt-get dist-upgrade

after reboot it picked up wifi thank you so much for your help

---

### Post by Bucky Ball on 2014-09-18
Good news. Please mark thread as solved to help others by following the second link in my signature. Good luck.

---

