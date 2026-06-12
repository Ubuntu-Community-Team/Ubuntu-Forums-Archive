---
title: "wireless not working 12.04 on MBP 1,2"
date: 2012-10-07
forum: Apple Hardware Users
---

### Post by deweyo on 2012-10-07
I've been using this older MBP 1,2 as a triple boot machine - OS 10.6.8, Meercat & XP in that boot order for several years now. Meercat always worked fine but not long ago I upgraded to 11.04 but was disappointed with long boot times. Everything did work tho so I then upgraded to 11.10 hoping for a better experience. No joy! Then I upgraded to 12.04 after reading all the positive reviews. Well I didn't get to explore it very much as it was quickly obvious that my wireless connection within Ubuntu would connect after entering my WPA key and then seconds later disconnect and ask me again to enter my WPA. I've searched the forums but it seems no one is using a MBP as old as mine. There are posts that refer to an area that lists compatible versions to various machines but I'll be damned if I can find it!

Bottom line - can this connection problem be fixed with 12.04 on my machine or should I go back to an older version like Meercat which worked great and was faster than the newer versions I tried. If it is the latter, how would I go about doing that? I already tried booting from the same disk I originally used to install Meercat but for some reason it just hangs at the first screen that gives all the options for as long as I'm willing to wait, which was almost an hour. Please help!

---

### Post by Bucky Ball on 2012-10-07
Could you open a terminal and paste this in:

```
sudo lshw -C network
```

Post the result here, please. ;)

Things can get a bit messy with direct upgrades, especially after a few, but if it was working previously I do like your chances.

---

### Post by deweyo on 2012-10-08
Sorry it took so long. Been a long day.
Ran the script but fumbled a lot figuring out how to save the output to a flash drive so I could paste it in here, but I did eventually figure it out.

dewey@dewey-MacBookPro:~$ sudo lshw -C network
[sudo] password for dewey: 
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 22
       serial: 00:16:cb:98:3f:b0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:98200000-98203fff ioport:2000(size=256) memory:98800000-9881ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:f2:43:43:fc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:98100000-9810ffff
dewey@dewey-MacBookPro:~$ 

I may be way off but it appears that it sees my wireless card as a PCI card, which of course is not the case - I think. Anyway, I'm curious to know what you see here. 

Thanks in advance - Dewey

---

### Post by varunendra on 2012-10-09
Hi deweyo,

The reason it is listed as a PCI device is because it is using a PCI bus (even though it is not a 'PCI card') which is normal.

While bucky ball returns, please try this:
```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k nohwcrypt=1
```then retry connecting. If that works we'll make this change permanent. If not, then please download and run 'wireless_script' (courtesy wild man, dave and others who contributed) as follows :
[COLOR=#000000][FONT=Ubuntu]```
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu]and post back the contents of the "netinfo.txt" file it creates in your home directory. It will give us a detailed info about your wireless settings.

PS:
Please post your output codes within [ code] .. and .. [ /code] tags to put them in a nice box as above. It also preserves the output formatting. To do so, just click on **#** at the edit box to auto-generate the tags, then copy-paste the output in-between the tags.
[/FONT][/COLOR]

---

### Post by deweyo on 2012-10-09
Varun - I ran those 2 scripts but the problem remains. 


[dewey@dewey-MacBookPro:~$ sudo modprobe -rfv ath5k
[sudo] password for dewey: 
rmmod /lib/modules/3.2.0-31-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.2.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-31-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-31-generic/kernel/net/wireless/cfg80211.ko
dewey@dewey-MacBookPro:~$ sudo modprobe -v ath5k nohwcrypt=1
insmod /lib/modules/3.2.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-31-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1
dewey@dewey-MacBookPro:~$ 
]

Not sure this is the format you were looking for - best I could do.

I assume the third script was meant to be written and sent in Ubuntu. Without a connection tho, I don't how it's possible. (I did try it anyway). I may have to drive an hour one way to pick up an ethernet cable and try connecting that way. 

Dewey

---

### Post by Bucky Ball on 2012-10-09
An ethernet cable is definitely going to help ... ;)

Who knows, an update/upgrade (packages, not OS) might fix ...

---

### Post by deweyo on 2012-10-09
I called my only neighbor about 2 miles away and his wife had one (cable) from many years ago. The plastic sheath is so hard I thought it might snap as I tried to straightened it out, but it's connected & working so here's the output from the script.

[dewey@dewey-MacBookPro:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-10-09 20:37:49--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 23.23.132.187, 50.16.240.166, 107.20.182.97, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|23.23.132.187|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0.001s  

Last-modified header missing -- time-stamps turned off.
2012-10-09 20:37:50 (1.18 MB/s) - `wireless_script' saved [1555/1555]

[sudo] password for dewey: 
dewey@dewey-MacBookPro:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script]

Doesn't look like there's any useful info that I can see but I'll let you decide that.

Dewey

---

### Post by deweyo on 2012-10-09
I did a bit more searching and discovered that the script in question generated a file in my home folder that contains what I'm sure you were looking for. Thanks for your patience.

[********** info trace ****************



**** uname -a ****


Linux dewey-MacBookPro 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:17:36 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)
    Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053 [11ab:5321]
    Kernel driver in use: sky2
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Apple Inc. AR5BXB6 802.11abg Wireless Mini PCIe Card [106b:0086]
    Kernel driver in use: ath5k


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 002 Device 002: ID 05ac:0217 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 001 Device 008: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)


**** iwconfig ****


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dm_crypt               22528  0 
btusb                  17912  2 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
rfcomm                 38139  12 
bnep                   17830  2 
bluetooth             158438  23 btusb,rfcomm,bnep
hid_apple              13166  0 
applesmc               18978  0 
input_polldev          13648  1 applesmc
binfmt_misc            17292  1 
appletouch             17318  0 
arc4                   12473  2 
isight_firmware        12586  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
usbhid                 41906  0 
ath5k                 145127  0 
ath                    19387  1 ath5k
hid                    77367  2 hid_apple,usbhid
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
mac80211              436455  1 ath5k
tpm_infineon           13200  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  3 ath5k,ath,mac80211
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
apple_bl               13425  0 
soundcore              14635  1 snd
lm63                   13998  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
uas                    17828  0 
usb_storage            39646  1 
radeon                733718  3 
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
video                  19068  0 
sky2                   49545  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    09FX08016856:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WEP


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"09FX08016856"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000031650f5fce9
                    Extra: Last beacon: 2108ms ago
                    IE: Unknown: 000C303946583038303136383536
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search westell.com


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


**** dmesg ****


[   24.751023] ath5k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

[   24.751039] ath5k 0000:03:00.0: setting latency timer to 64
[   24.751087] ath5k 0000:03:00.0: registered as 'phy0'
[   25.293402] ath: EEPROM regdomain: 0x65
[   25.293408] ath: EEPROM indicates we should expect a direct regpair map
[   25.293412] ath: Country alpha2 being used: 00
[   25.293414] ath: Regpair used: 0x65
[   25.315749] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)
[   25.812800] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.813388] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************

]

Whew! That oughtta keep you busy!

Dewey

---

### Post by varunendra on 2012-10-10
deweyo,
Um.. I think you realize it very well that it wasn't my patience but my 'absence' that provided you 'enough' time to try all that stuff (although I AM a very patient guy..;))

Anyway, now that you have a wired connection, you should try what Bucky Ball suggested. That is, do an update to see if newer packages may fix it automatically for you.

As for the code part, sorry but you misunderstood. Let me show you an example:

If I post the output of command - '**[COLOR="DarkRed"]echo -e "first line\nsecond line\nthird line"[/COLOR]**' without code tags, it will look like :
[COLOR="DarkRed"]first line
second line
third line[/COLOR]

.. that is the way you are posting.
But if I add the mentioned tags in the beginning and the end of the above output so that they look like - 
[COLOR="DarkRed"][noparse]```
first line
second line
third line
```[/noparse][/COLOR]
then, in the post it will look like :
```
first line
second line
third line
```

The **#** symbol at the top of edit box (in which you create your new posts) makes that easy by automatically creating those tags. You can use it in two ways:
[LIST=1]
[*]Just click on the **#**, then copy-paste the outputs in-between the generated tags.
[*]Using your mouse cursor, highlight an already existing portion of your post (which is an output of some command), then click on **#** to automatically add those tags at the beginning and end of the highlighted part.
[/LIST]
I'd suggest you to try this right now on your previous posts to enclose the outputs in the [ code] tags.
(you can not edit your posts after 7 days)

---

### Post by deweyo on 2012-10-10
Hi again. I checked for updates but nothing for wireless.

Now I'll try the code thing -  

Code
```
Linux dewey-MacBookPro 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:17:36 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

```Somehow I don't think that's it - Dewey

---

### Post by deweyo on 2012-10-10
Varun -

I did a little more poking around in simple sections - like my wireless setup. The whole time (even while using a wired connection) every 10 - 15 seconds the alert box asking me for my WEP key would keep coming back. Really annoying!
I went into the connection menu, chose wireless, and then edit. I filled in the WEP key box and clicked save. The connection seemed to hold so I disconnected the wired connection and then unplugged it. So far so good. I'm not going to call it solved yet but it's looking hopeful. I'll restart into the Mac OS and play around a bit and then restart back into Ubuntu and then we'll see.

Dewey

---

### Post by varunendra on 2012-10-11
> **deweyo said:**
> I'll restart into the Mac OS and play around a bit and then restart back into Ubuntu and then we'll see.
..And I'll eagerly await.

Not to discourage you, but I've seen that stuff like authentication, getting IP from dhcp etc. regarding wireless works better (in fact instantly) if you are simultaneously connected via cable. But once you are wireless-only, same old story. But yes, saving the key in network manager is a good idea (duh, why didn't I ask it before!).

---

### Post by deweyo on 2012-10-11
Now that you've brought it up, yes, I do remember having to have a cable connected initially to configure an airport. 

Still no problems so I'd say it's solved.

I should have looked into those settings early on and could have saved us both a lot of time - sorry. I'm so used to the Mac upgrades which are about as low stress as you can get. Never had an issue with saving and transferring settings.

I have to say, now that this one issue is fixed, this version appears to be considerably better (faster) than the last two. 

Regardless, let me say thank you for all your help. It's much appreciated.

Dewey

---

### Post by Bucky Ball on 2012-10-11
Great news! Please mark thread as 'Solved', if when you're happy it is, from Thread Tools to help others. ;)

If the details are sticking in NM then all should be good.

---

