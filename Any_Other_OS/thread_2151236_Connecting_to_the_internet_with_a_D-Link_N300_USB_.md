---
title: "Connecting to the internet with a D-Link N300 USB Dongle"
date: 2013-06-03
forum: Any Other OS
---

### Post by Placidia428 on 2013-06-03
I am running Linux Mint 14

```
placidia@Sandbox ~ $ uname -a
Linux Sandbox 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I recently bought a D-Link N300 dongle, to replace a slower USB dongle. The N300 could connect to the network, but could not reach the Internet.

Here is the output to nm-tool

```
placidia@Sandbox ~ $ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan2  [Tara] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           no
  HW Address:        C8:D3:A3:A3:0A:A8

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TIPI:            Infra, E8:40:F2:36:7D:A7, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WPA2
    heatherdenis:    Infra, 00:22:2D:6F:7E:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 43 WPA
    PS3-9333553:     Infra, 8C:7C:B5:D4:93:D9, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WPA
    *Tara:           Infra, E8:40:F2:4B:73:86, Freq 2462 MHz, Rate 54 Mb/s, Strength 99 WPA WPA2
    BELL381:         Infra, 2C:E4:12:A1:3E:D7, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2

  IPv4 Settings:
    Address:         192.168.0.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             64.71.255.204
    DNS:             64.71.255.198


- Device: wwan0  [Rogers Default] ----------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            sierra
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         25.48.61.154
    Prefix:          24 (255.255.255.0)
    Gateway:         25.48.61.154

    DNS:             64.71.255.205
    DNS:             64.71.255.253


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:24:81:ED:7E:2C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

And lsusb yields

```
placidia@Sandbox ~ $ lsusb
Bus 001 Device 005: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
Bus 002 Device 003: ID 1199:68a3 Sierra Wireless, Inc. MC8700 Modem
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

```

I am currently connected with a Sierra Wireless dongle - which is expensive. So I would like to get the broadband working.

Can anyone suggest anything?

---

### Post by Placidia428 on 2013-06-03
I solved my own problem. The D-Link N300 needs the Realtek RTL8191SU drivers. These can be found [here]("http://www.realtek.com.tw/downloads/searchView.aspx?keyword=rtl8191su"). Unzip the file, change the permissions on install.sh to allow for execution. Then execute the install script. It works.

---

