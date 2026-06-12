---
title: "[SOLVED] Atheros AR9485 ath9k connectivity problems"
date: 2014-07-07
forum: Any Other OS
---

### Post by Gfurst on 2014-07-07
Hello fellow linux nerds,
I'm trying to get rid of my wired eth cable and use my wireless Atheros card. 
This  is a new setup, build up a desktop PC with latest mid-range hardware,  the card in question is TP-link with Atheros AR9485 chip, which  apparently uses the ath9k driver.
The wireless works but has very bad connectivity and intermittent disconnects, asking for password again, etc. Very similar to issues people had [here]("https://bbs.archlinux.org/viewtopic.php?id=161305&p=1") and [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188").
Apparently this was common issue with kernel 3.8 and 3.9, fixed on kernel 3.11.
However I am currently on 3.15 liquorix version, had previously used 3.13 and 3.14( since this was a fresh install), and they all presented this issue.

I've already tried the below without any improvements:
```
modprobe -r ath9k
modprobe ath9k nohwcrypt=1
```

This is a semi-fresh installation of debian Jessie(testing), i know its not Ubuntu, but guys here are very good at solving issues.
The connection appears as +-40% signal quality, only 1mb link, and must at most 4 meters in distance with walls in the way.
Other devices and Pc had no issue.

---

### Post by jeremy31 on 2014-07-07
What router(brand/model) are you trying to connect to?

And post the resulting wireless-info file that this script generates ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
As it will help in diagnosing the issue[/FONT][/COLOR]

---

### Post by Gfurst on 2014-07-08
Hey jeremy31, thanks for taking a interest. My router is a D-link DIR-600
Quick note on the below file that the wlan0 interface, 1Mb transfer rate, ipv4 0.0.0.0 I wouldn't be using the internet without wired cable.
I have to set reserved ip address for my physical address or it wouldn't work at all.
This router isn't the best and had issues in the past, I've thinking about installing some open-source firmware on it, could this make difference?

```
########## wireless info START ##########

##### release #####

Distributor ID: Debian
Description:    Debian GNU/Linux testing (jessie)
Release:        testing
Codename:       jessie

##### kernel #####

Linux guiu-desktop 3.15-3.dmz.1-liquorix-amd64 #1 ZEN SMP PREEMPT Sat Jul 5 21:18:05 UTC 2014 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
        Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
        Kernel driver in use: r8169

05:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
        Subsystem: Qualcomm Atheros Device [168c:3118]
        Kernel driver in use: ath9k

##### lsusb #####

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1a2c:0023 China Resource Semico Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID abcd:1234 Unknown 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### lsmod #####

ath9k                  85082  0 
ath9k_common           11328  1 ath9k
ath9k_hw              410493  2 ath9k_common,ath9k
ath                    21702  3 ath9k_common,ath9k,ath9k_hw
mac80211              521730  1 ath9k
cfg80211              478903  4 ath,ath9k_common,ath9k,mac80211

##### iw reg get #####

##### interfaces #####

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

##### resolv.conf #####

nameserver 201.17.128.73
nameserver 201.17.128.78

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Bittencourt] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    VIVO Wi-Fi:      Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Galo Doido:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 11 Mb/s, Strength 30 WPA2
    *Bittencourt:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    GVT-8E37:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA2
    M_CLAUDIA:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA2

  IPv4 Settings:
    Address:         0.0.0.0
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             201.17.128.73
    DNS:             201.17.128.78

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             201.17.128.73
    DNS:             201.17.128.78

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Bittencourt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000041782b2d8
                    Extra: Last beacon: 11ms ago
                    IE: Unknown: 000B42697474656E636F757274
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0016FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020040127A
                    IE: Unknown: DD960050F204104A0001101044000102103B000103104700102880288028801880A8801C7EE5963F1E10210012442D4C696E6B20436F72706F726174696F6E1023000D442D4C696E6B20526F75746572102400074449522D363030104200044E6F6E651054000800060050F20400011011001A576972656C657373204E2031353020486F6D6520526F75746572100800020080103C000101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706555320010B10
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"GVT-8E37"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002da500a510
                    Extra: Last beacon: 11ms ago
                    IE: Unknown: 00084756542D38453337
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010825C652AD23F66C31FA1B1A95469C0481021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD09001018020100000000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Galo Doido"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000369287a3c68
                    Extra: Last beacon: 11ms ago
                    IE: Unknown: 000A47616C6F20446F69646F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported

##### iwlist channel #####

##### modinfo #####

##### modules #####

fglrx

##### blacklist #####

[/etc/modprobe.d/blacklist-fglrx.conf]
blacklist radeon

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist hyperv_fb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2014-07-08
If you have had issues with the router in the past, I would do something with it first.  You could also change the security on the router to WPA2-AES instead of the mixed mode.
 if you are in Brazil
```
sudo iw reg set BR
``````
cat /etc/default/crda | grep -i regdomain=
```
I don't know if Debian Jessie has the crda file, if it does, you should edit it so the last line says REGDOMAIN=BR

---

### Post by coffeecat on 2014-07-08
*Thread moved to **Other OS/Distro Support**.*

---

### Post by Gfurst on 2014-07-08
> **jeremy31 said:**
> If you have had issues with the router in the past, I would do something with it first.  You could also change the security on the router to WPA2-AES instead of the mixed mode.
 if you are in Brazil
```
sudo iw reg set BR
``````
cat /etc/default/crda | grep -i regdomain=
```
I don't know if Debian Jessie has the crda file, if it does, you should edit it so the last line says REGDOMAIN=BR
Ok, now that you mention, I'd remember having trouble with that in the past, not sure if the same router though.
Manual wireless settings on the router are a bit limited:
802.11n,g,b (mixed) -- turn this to 802.11n only
Transmission rate is automatic (can't change it)
Channel width: 20 Mhz or 20/40Mhz, set it to 20Mhz only
Security mode WPA/WPA2 or disabled (only these two options)
However changing to 802.11n only, changes the cipher type to AES only ( instead of AES/TKIP).

Setting updated on the router, still unable to connect. Before it would state connected with no ip address (even though I marked "require ipv4 address"). Now it it will try for a minute and report unable to get ipv4 address.

Oh and I've set the nohwcrypt=1 and set to REGDOMAIN=BR, there was the crda file too. 
Without success after load the driver, also found this:
```
guiu@guiu-desktop:~$ dmesg | grep ath
ath9k 0000:05:00.0: enabling device (0000 -> 0002)
ath: EEPROM regdomain: 0x21
ath: EEPROM indicates we should expect a direct regpair map
ath: Country alpha2 being used: AU
ath: Regpair used: 0x21
ath9k: ath9k: Driver unloaded
ath: EEPROM regdomain: 0x21
ath: EEPROM indicates we should expect a direct regpair map
ath: Country alpha2 being used: AU
ath: Regpair used: 0x21

```
So I don't think the regdomain=BR worked, maybe its a different code?

---

### Post by jeremy31 on 2014-07-08
```
iw reg get
``````
cat /etc/default/crda | grep REGDOMAIN=
``` to see if they are correct

I checked this [http://en.m.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.m.wikipedia.org/wiki/ISO_3166-1_alpha-2) and BR is correct for Brazil and I only know of one other place it could be set and you should be able to check with ```
sudo cat /sys/module/cfg80211/parameters/ieee80211_regdom
```

---

### Post by Gfurst on 2014-07-08
humm ok:

'iw reg get' after boot
```
country US: DFS-UNSET
        (2402 - 2472 @ 40), (N/A, 30)
        (5170 - 5250 @ 80), (N/A, 17)
        (5250 - 5330 @ 80), (N/A, 23), DFS
        (5735 - 5835 @ 80), (N/A, 30)
        (57240 - 63720 @ 2160), (N/A, 40)

```
after iw reg set BR
```
country 98: DFS-UNSET
        (2402 - 2472 @ 40), (N/A, 20)
        (5170 - 5250 @ 80), (N/A, 17)
        (5250 - 5330 @ 80), (N/A, 23), DFS
        (5735 - 5835 @ 80), (N/A, 30)

```

grep from crda file
```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
REGDOMAIN=BR

```
but
```
guiu@guiu-desktop:~$ sudo cat /sys/module/cfg80211/parameters/ieee80211_regdom 
00

```

However: my dad was nagging me to get rid of the Ethernet cable crossing over the house, he insisted it was because of how I've placed my PC.
So after a shutdown and moving my PC around, for a closer spot, wireless is apparently working fine. Maybe it was the settings above combined needed a reboot, plus the router config.
I'll be moving it around either way just to make sure its not the spot.
Right now I'm connected through it with a 50% signal strength 26Mbits.

---

### Post by /ADM on 2014-07-10
I have that same wireless chip in my laptop and most of the distro's that do not contain 'bleeding edge' or at least a few months old packages will not work with it.  Debian's releases are so ancient that it does not even work with my laptop at all, the kernel is simply too old to support anything meaningful.  Ubuntu 14.04 worked out of the box, as did Lubuntu 14.04.

On older kernels like 3.10 (in my slackware box) it is a chore to get it recognised.  I think these drivers for the AR94xx series are quite new and are only just being supported in the last year or so.  For other OS's even FreeBSD is the only BSd to support it (and only in the last 6 months).  When it does work it never is very strong, I guess it will improve gradually but for me at least the strength is half of what it was in Windows (before I obliterated it's partition) =)

---

### Post by Gfurst on 2014-07-10
Actually I'm using Debian Jessie, which is the testing version of Debian with pretty up-to-date packages, stock kernel was 3.14, I've used the smxi scripts to upgrade this to the liquorix kernel 3.15.
wi-fi is now working really stable, with very bad reception and some times really low speed, but its stable none-the-less.
I don't really know if the above solutions (the nohwcrypt option and the REGDOMAIN=BR) but setting the router to using only one encryption method surely helps.
Perhaps setting proper regdomain for the frequencies can help with the signal strength. Still I'm going to tag this thread as solved.
Maybe someone will this useful.

---

