---
title: "No WiFi when booting from live USB"
date: 2017-04-18
forum: Any Other OS
---

### Post by sysone on 2017-04-18
When booting from live 'tails' or 'TENS-1.7.0'  or similar, everything seems to be fine except for wireless WiFi which does not show the existing WiFi networks.
In Software & Updates , I see:  'This device  is using an alternative driver. Using Processor microcode firmware for Intel CPUs from intel-microcode  (proprietary) '

~$ lspci:
```
~$ lspci:
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 79)
~$ 

```
Network
Pastebin successful:   [http://paste.ubuntu.com/24403007/](http://paste.ubuntu.com/24403007/)

Any help very much appreciated.
Please note that I am **NOT **a savvy user and would need step by step instructions.
Thanks

---

### Post by chili555 on 2017-04-18
Here is what we see in your paste:> [    7.812037] wlp1s0: authenticate with <MAC 'AirLink-2.4GHZ' [AC1]>
[    7.817474] wlp1s0: send auth to <MAC 'AirLink-2.4GHZ' [AC1]> (try 1/3)
[    7.834203] wlp1s0: authenticated
[    7.837227] wlp1s0: associate with <MAC 'AirLink-2.4GHZ' [AC1]> (try 1/3)
[    7.843427] wlp1s0: RX AssocResp from <MAC 'AirLink-2.4GHZ' [AC1]> (capab=0x411 status=0 aid=1)
[    7.846740] wlp1s0: associated
[    7.846767] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes readyAs well as:> wlp1s0    IEEE 802.11  ESSID:"AirLink-2.4GHZ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'AirLink-2.4GHZ' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:156   Missed beacon:0
And also:> SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
AirLink-2.4GHZ      <MAC 'AirLink-2.4GHZ' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
AirLink-5GHz        <MAC 'AirLink-5GHz' [AC8]>  Infra  36    5180 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
optimumwifi         <MAC 'optimumwifi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  --         no        
C8942E              <MAC 'C8942E' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
C-NET-GUEST         <MAC 'C-NET-GUEST' [AC4]>  Infra  2     2417 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
WhiteDolphin-guest  <MAC 'WhiteDolphin-guest' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  --         no        
C-NET               <MAC 'C-NET' [AN7]>  Infra  2     2417 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
optimumwifi         <MAC 'optimumwifi' [AC10]>  Infra  36    5180 MHz  54 Mbit/s  20      &#9602;___  --         no        
WhiteDolphin        <MAC 'WhiteDolphin' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        
C8942E              <MAC 'C8942E' [AC9]>  Infra  36    5180 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        
Comphome            <MAC 'Comphome' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        Although we see a few things that we'd suggest that you do to tweak your  setup, I'm not sure that your wireless could be working much better!

Please explain.

---

### Post by sysone on 2017-04-18
Wireless works well in my Ubuntu 16.04.2 LTS..
Even when booting from a USB with live Ubuntu 16.04  iso, it boots well and wireless works well.

But when booting from a USB with live PENS, it boots well and works well,  except for wireless which does not show any networks available. Same for other Linux distributions.

As i said:[B]
			 			'When booting from live 'tails' or 'TENS-1.7.0'  or similar,  everything seems to be fine except for wireless WiFi which does not show  the existing WiFi networks.'[/B]

---

### Post by chili555 on 2017-04-18
> When booting from live 'tails' or 'TENS-1.7.0' or similar, everything seems to be fine except for wireless WiFi which does not show the existing WiFi networks.'Sorry if I misunderstood. We know nothing about TENS.

---

### Post by QIII on 2017-04-18
Moved to ***Any Other OS***.

While we are happy to have you ask a question about other OSes here -- and we certainly hope someone can help you -- the general support areas of the Ubuntu Forums are intended for support for official Ubuntu flavors.

---

