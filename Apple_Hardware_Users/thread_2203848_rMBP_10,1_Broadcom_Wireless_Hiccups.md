---
title: "rMBP 10,1 Broadcom Wireless Hiccups"
date: 2014-02-05
forum: Apple Hardware Users
---

### Post by Umbra Diaboli on 2014-02-05
Hello,

I have Ubuntu 13.10 installed on my rMBP 10,1. Everything has been working perfectly except for the WiFi.

My signal bar looks like this:

[IMG]http://i.imgur.com/Y9Rlyr3.png[/IMG]

Browsing is good, however, every 1-2 minutes the internet stops completely for about 20 seconds, and there is no data transfer at all. When this happens the signal bar goes full:

[IMG]http://i.imgur.com/6u45MPp.png[/IMG]

I am using Broadcom Wireless Driver bcmwl (6.30.223.141+bdcom-0ubuntu1). My kernel is 3.11.0-15

Has anyone come across this problem and found a solution?

Thanks in advance :D

BTW, I've tried reinstalling the driver using synaptic, it didn't help :(

---

### Post by varunendra on 2014-02-06
May we see the output of -
```
lspci -nnk | grep -iA2 net
``` ?? Or, if it happens to be on a USB bus, then -
```
lsusb
```

---

### Post by Umbra Diaboli on 2014-02-07
Hi,

Here is the output:

```
03:00.0 Ethernet controller [0200]: Broadcom Corporation Device [14e4:16a3] (rev 10)
    Subsystem: Broadcom Corporation Device [14e4:16b4]
03:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00ef]
    Kernel driver in use: wl
```

It has misteriously been working fine for the past day, but I've had this problem before. When it happens, it becomes impossible to browse the internet. This last time I've had the problem, it lasted for about 5 days.

Cheers

---

### Post by varunendra on 2014-02-07
> **Umbra Diaboli said:**
> ```
04:00.0 Network controller [0280]: Broadcom Corporation **BCM4331** 802.11a/b/g/n** [14e4:4331] **(rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00ef]
    Kernel driver in use: **[COLOR="#FF0000"]wl[/COLOR]**
```

Please try what I just suggested in this post : [http://ubuntuforums.org/showthread.php?t=2204097&p=12922248#post12922248](http://ubuntuforums.org/showthread.php?t=2204097&p=12922248#post12922248)

---

### Post by Umbra Diaboli on 2014-02-07
Hi,

Thanks for your response. I'm not with my rMBP right now. But as soon as I get home, I'll check what you suggested in the other post :D 

Sorry for any inconvenience. 

Cheers

---

### Post by Umbra Diaboli on 2014-02-08
Hi,

I tried what you said. Everything seems to be working perfectly :D

I'll follow up if I run into further problems.

Thanks very much!

---

### Post by varunendra on 2014-02-08
You're welcome! :)

Be aware that the "Additional Drivers" program proposes the sta or "wl" driver for installation, so don't accept its proposal, the native one is better for your card.

---

### Post by Quackers on 2014-02-11
Interesting. I have the same rMBP and installing linux-non-free did nothing at all. The only way I can get wifi is to install bcmwl after dims. It works ok but gets a little slow sometimes.
Maybe I did something wrong  :(

---

### Post by varunendra on 2014-02-12
> **Quackers said:**
> Interesting. I have the same rMBP and installing linux-non-free did nothing at all. The only way I can get wifi is to install bcmwl after dims. It works ok but gets a little slow sometimes.
Maybe I did something wrong  :(

Hi Quackers! So good to see you here. :)

Sorry I didn't notice earlier that you had posted. May I suggest to check out the b43 again and make sure it is not blacklisted?

As you can see yourself [here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices"), this and a few other Broadcom cards are supported by both "wl" and "b43" modules. It is just that most of us wireless 'bugs' here prefer the b43 in such situations, not just because it is open-source, but because it practically works better (usually.. :/).

If you wish to try that (doesn't cost much time if you have a wired connection available) -
```
sudo apt-get purge bcmwl-kernel-source
```
..followed by a reboot, because sometimes the "wl" driver refuses to unload with a simple 'modprobe -r'.

Assuming you already have correctly installed the firmware (firmware-b43-installer, or linux-firmware-nonfree), the reboot should automatically load the "b43" driver. If the wifi fails to work, or as good as the bcmwl, I'd be glad to help dig deeper if you wish. Or you can choose to switch back to the bcmwl again.

The keyword in this case is - "Usually" :)

---

### Post by Quackers on 2014-02-13
Hi varunendra :D
I'll reboot in to Ubuntu and have a mooch around. (Sadly I don't have a wired connection available - no ethernet socket and I'm not sure my Mac has ethernet card either).

---

### Post by Quackers on 2014-02-13
Ok, varunendra I followed your instructions and then rebooted.
It fired up with no wifi symbol in the top bar but it did have a "two screen" type icon (I think it used to be the ethernet symbol).
I clicked on that and my network was listed as connecting. It took a while to connect and now my wifi symbol is showing. I have internet now, however it's quite slow to connect to the couple of sites I've tried and it's also slow to load pages.
Also even when a page/site is loaded the open tab shows the orange thing still spinning for a while as if it's still connecting.
But it is working now, at least :-)
Any advice for me?
Thanks.

---

### Post by varunendra on 2014-02-13
Yup, I'd like to see overall current settings. I think you've already guessed what my next sentence is going to be :P

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. :-\"

---

### Post by Quackers on 2014-02-13
Yikes! 8MB of updates just took a full minute to download! Usually that would take about 15 - 20 seconds.

varunendra, can I run the script on my present wifi connection? I have no wired connection available.

---

### Post by varunendra on 2014-02-13
How about a 4 KB/s speed? That's what I get on my awesome GPRS connection when it is good :P

Please see my previous post.

---

### Post by Quackers on 2014-02-13
Connection timed out
```
mike@mike-MacBookPro:~$ wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-02-13 13:46:36--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 23.23.92.89
Connecting to dl.dropbox.com (dl.dropbox.com)|23.23.92.89|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-02-13 13:46:37--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... failed: Connection timed out.
wget: unable to resolve host address &#8216;dl.dropboxusercontent.com&#8217;

```

---

### Post by varunendra on 2014-02-13
Try the offline method (Method 2 in the linked post).

---

### Post by Quackers on 2014-02-13
Sorry, network became "out of range" - not seen that before.
Here's the output
```

*************** info trace ***************

***** uname -a *****

Linux mike-MacBookPro 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

03:00.0 Ethernet controller [0200]: Broadcom Corporation Device [14e4:16a3] (rev 10)
	Subsystem: Broadcom Corporation Device [14e4:16b4]
03:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
	Subsystem: Apple Inc. AirPort Extreme [106b:00ef]
	Kernel driver in use: bcma-pci-bridge

***** lsusb *****

Bus 002 Device 005: ID 05ac:0263 Apple, Inc. Apple Internal Keyboard / Trackpad (MacBook Retina)
Bus 002 Device 008: ID 05ac:8286 Apple, Inc. Bluetooth Host Controller
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8510 Apple, Inc. FaceTime HD Camera (Built-in)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:"SKY40D6B"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:24   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

b43                   387322  0 
mac80211              597268  1 b43
cfg80211              480503  2 b43,mac80211
ssb                    62057  1 b43
bcma                   46699  1 b43

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [SKY40D6B] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    PlusnetWirelessC4B0E4: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    *SKY40D6B:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 98 WPA2
    SKY54935:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"SKY40D6B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000df31819
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0008534B593430443642
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A0001101044000102103B0001031047001062C9C39482D5BFB2D281AC1FB831E2381021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"PlusnetWirelessC4B0E4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 0015506C75736E6574576972656C657373433442304534
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD8F0050F204104A00011010440001021041000100103B000103104700106DC70B5224FE5166B3B7D5ACBF62670D1021000B546563686E69636F6C6F721023000E546563686E69636F6C6F72205447102400043538326E104200093133303956463432451054000800060050F204000110110012546563686E69636F6C6F722054473538326E100800020084103C000101
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"SKY54935"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b96415ce25
                    Extra: Last beacon: 28580ms ago
                    IE: Unknown: 0008534B593534393335
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101090003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010024FF7F
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-01C1C3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000761b0e9a83
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D303143314333
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000F7A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706474220010B10
                    IE: Unknown: DD1E00904C330C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000400000000000000000000000000000000000000
                    IE: Unknown: DD970050F204104A0001101044000102103B00010310470010BC329E001DD811B286019094E401C1C310210013442D4C696E6B20436F72706F726174696F6E2E1023001C442D4C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110008442D4C696E6B4150100800020084103C000100


***** resolv.conf *****

nameserver 127.0.1.1
search Home

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     9B797CFD1C70935B62C35EE
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
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

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:0x4331 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4331 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    5.954527] bcma: bus0: Found chip with id 0x4331, rev 0x02 and package 0x09
[    5.954561] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[    5.954587] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[    5.954637] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[    6.004557] bcma: bus0: Bus registered
[    6.183476] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[    6.183851] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[    6.802044] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[    6.862445] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.862791] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.381640] wlan0: authenticate with <MAC address removed>
[   32.401419] wlan0: send auth to <MAC address removed> (try 1/3)
[   32.403043] wlan0: authenticated
[   32.405000] wlan0: associate with <MAC address removed> (try 1/3)
[   32.410595] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   32.410883] wlan0: associated
[   32.410891] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************

```

---

### Post by varunendra on 2014-02-13
Everything looks pretty solid, maybe too solid ! Can it be that you are too close to the Access-Point?

There is a 'Sweet Spot' regarding the distance from the access-point, which is dependent on the quality of both transmitting and receiving units (and driver performance too, hence may differ for different OSes on the same unit as far as I know, although I know very little about this). As per my knowledge, too close a distance may cause 'Packet-Bouncing' sometimes.

If everything is good, and the above is not applicable, we may try a forced speed. For example, to try 24 Mb/s -
```
sudo iwconfig wlan0 rate 24M
```
The supported speeds, as per the result of iwconfig (reasonably better ones), are 5.5 Mb/s; **11 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s**; 54 Mb/s; 6 Mb/s; 9 Mb/s; **12 Mb/s; 48 Mb/s**

For now, these are the only things that come to mind. If they don't help, maybe time to switch back to the sta driver and let us know how better it practically is.

**PS:**
Based on a recent feedback on a different but similar problem, you may also try setting the **MTU** value to **1492** or **1392** in Network Manager. That also helps when the frame size is a problem for the router or 'Any' device in the traffic route.

---

### Post by Quackers on 2014-02-13
Ok thanks varunendra I can try that.
I'm about 6 or 7 feet from the router, which is where I always am.
I notice in the blacklist output that 
blacklist bcm43xx
appears. Is that normal?
It's currently connecting slowly then drops out after about 2 minutes and then shows that the network is out of range and needs rebooting to re-connect.

Currently back in OSX so will reboot and try your last.

---

### Post by varunendra on 2014-02-13
> **Quackers said:**
> I notice in the blacklist output that 
blacklist bcm43xx
appears. Is that normal?


Yes that is normal, it was some old version of broadcom driver which is depreciated now.

Please also see my edit in my previous post when you try again. :)

---

### Post by Quackers on 2014-02-13
Hmm, it's now showing strength as "excellent".
MTU is set to "automatic" and I haven't changed anything yet.
If it drops out again shortly I'll try the rate change first.

---

### Post by Quackers on 2014-02-13
Connection dropped out again. I turned off wifi and then turnedf it back on. Wifi connected again and it's still connected after 5 minutes or so  :D
Still very slow though.
I'll do some playing around but if things don't improve I'll need to go back to bcmwl as it's largely unusable at the moment.
We'll see.
Thanks for your help varunendra ):P

---

### Post by varunendra on 2014-02-13
No problem. :)

A few broadcom chips are a matter of hit or miss, especially those that are supported by both drivers. Usually when one doesn't work, the other does very well. But some of its chips can be dodgy at times, although this one wasn't (still isn't) in my list of such 'dodgy' chips.

I hope the current connection is at least good enough to let you download the 'bcmwl-kernel-source' package if required. Else we have other ways, fortunately. :D

---

### Post by Quackers on 2014-02-13
Lol, I have the bcmwl driver stored in case of accidents  :)

---

