---
title: "BIG Wifi Problem"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by marufaberlin on 2008-03-10
Hi, ... I have this problem for quite a while now, but it started when I decided to run a complete new update (about 2-3 months ago). Since then, my wifi doesn't work. nm-applet does not start. The problem is that the module iwlwifi_rc80211_simple doesn't work. When I try to insert it using modprobe I get the following:
```

$ sudo modprobe iwlwifi_rc80211_simple 
FATAL: Error inserting iwlwifi_rc80211_simple (/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_rc80211_simple.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg gives me the following (excerpt):

```
$ sudo dmesg
...
[ 1375.444000] ieee80211_init: failed to initialize WME (err=-17)
[ 1375.460000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 1375.460000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[ 1375.460000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[ 1375.460000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
...
```

what the hell (sorry for my language, but I'm frustrated:-?) should I do???

Hoping that someone hears my plea for help (any of which is welcome),

marufaberlin

---

### Post by wieman01 on 2008-03-10
What hardware have you got and what chipset is your device?

Please post the results of:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces

---

### Post by marufaberlin on 2008-03-10
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:52:79:D2:1D
                    ESSID:"Sporthalle"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-82 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : none TKIP
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : none TKIP
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004ef3a289d5
          Cell 02 - Address: 00:09:5B:68:13:76
                    ESSID:"HS-Libwireless"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-70 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000835485b48aa
```
```
auto lo
iface lo inet loopback



iface eth0 inet static
address 192.168.101.244
netmask 255.255.255.0
gateway 192.168.101.10

auto eth0

```
```
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:04:09.0
       logical name: wmaster0
       version: 00
       serial: 00:19:db:96:f6:e8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

```

---

### Post by wieman01 on 2008-03-10
This is a Ralink chipset so I am sure the updates have messed with your driver. That's a fairly common issue... 

Please do the follow for me. Update "/etc/network/interfaces" so that it reads:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.101.244
netmask 255.255.255.0
gateway 192.168.101.10

auto wlan0
iface wlan0 inet dhcp
Then restart the PC and see if Network Manager picks up the device and lets you connect to your network e.g. "Sporthalle". 

If it fails, the only option left is my Ralink tutorial (signature). That will replace the current driver "rt61pci" with ndiswrapper and the native Windows driver which works well for the "rt61pci".

Are you on 64-bit Ubuntu by chance?

---

### Post by marufaberlin on 2008-03-10
Yeah,... im on 64bit. But can I do without restarting? I do not want to disconnect from my local lan and I have some important processes that cannot be stopped right now?

---

### Post by wieman01 on 2008-03-10
It will be impossible without restarting the PC, however, you could do so at a later stage. I will still be around to help you out.

As for 64-bit... This might create an issue while deploying the Windows driver using 'ndiswrapper'. For certain you need to get hold of the 64-bit version of the driver in the first place before you install it. But let's look into the matter after you have tried the solution described above (after restarting the server).

---

### Post by marufaberlin on 2008-03-10
Ah, I see you're staff. At that opportunity, I would like to ask you what's up with the showthanks.php file on your server? I always get a blank screen.

---

### Post by wieman01 on 2008-03-10
Well, you should read [this]("http://ubuntuforums.org/showthread.php?t=702596") for more. It just has not been implemented yet, hence the empty page. They will do so later this year, but as I understand there is no fixed schedule.

---

### Post by marufaberlin on 2008-03-10
Thanks :lolflag:.

---

### Post by marufaberlin on 2008-03-10
Ok, I rebooted, didn't bring no help. Think I'll have a look at that tutorial.

---

### Post by marufaberlin on 2008-03-10
But I haven't got dapper, I've got gutsy.

---

### Post by wieman01 on 2008-03-10
My guide is for Gutsy users. You'll see. Please get ahold of the 64-bit Windows driver.

---

### Post by marufaberlin on 2008-03-14
Ok I got the wifi running, but now nm-applet does not work. Is there any program I could use to search for and connect to wireless lans? I know there is wlassistant, but that doesn't work with WPA.

---

### Post by dca on 2008-03-14
You could always try 'WICD' as a replacement to NM...
 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by marufaberlin on 2008-03-14
Ok, I'll try that.

---

### Post by marufaberlin on 2008-04-08
I just noticed that since my wifi works again, my card doesn't work with tools like airodump-ng, airmon, etc... How can I get them to work?

---

### Post by wieman01 on 2008-04-08
Your adapter either does normal wifi OR does packet reinjection, etc. (i.e. airodump). Patching your driver for packet reinjection automatically renders it useless for anything else...

---

### Post by marufaberlin on 2008-04-10
But I could use the card normally **and** use airodump-ng. :-?

---

### Post by marufaberlin on 2008-04-15
Can I help implementing it somehow?

---

