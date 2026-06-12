---
title: "Acer C710 Chrubuntu 12.04 ath9k / AR9462 problems recognizing wireless and ethernet"
date: 2014-02-26
forum: Any Other OS
---

### Post by Taren.lewis on 2014-02-26
So I've been through quite a few threads trying different commands and nothing seems to have worked for me. I'm open to any and all suggestions, and please understand that I don't really know what I'm doing. I just installed chrubuntu again tonight after having some issues with losing drive space and the OS crashing. I seem to remember previously having this problem, and I believe I was able to download a driver on a different computer and transport it via USB. When I click on the wireless icon in the top right it says "No network devices available". Here are some commands I used:


```
user@ChrUbuntu:~$ lspci -nn | grep 0280

01:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
```

 
```
user@ChrUbuntu:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for user:

options ath9k nohwcrypt=1
```


```
user@ChrUbuntu:~$ sudo modprobe -rfv ath9k
```




```
user@ChrUbuntu:~$ sudo modprobe -v ath9k

insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
FATAL: Error inserting ath9k (/lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): No such device
```

```
user@ChrUbuntu:~$ sudo iwconfig wlan0 power off

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.
```






I also tried to download a driver again this time and extract it to the home folder as per instructions [http://askubuntu.com/questions/121932/ath9k-driver-reinstallation](http://askubuntu.com/questions/121932/ath9k-driver-reinstallation) here, but I was having trouble with permissions allowing me to extract to the place I believed was correct and was unable to install the driver.

Thanks again. I know this may have been answered somewhere, but I haven't been able to find anything that worked specifically for my system.

---

### Post by Bucky Ball on 2014-02-26
*Thread moved to **Other OS/Distro Support**.*

Chrubuntu is not officially supported in the main areas of the forums. Good luck.

PS: You can add [code][ /code] tags manually or by clicking 'Go Advanced', marking out the code and clicking the '#' icon.

---

### Post by varunendra on 2014-02-27
Welcome to the forums Taren.lewis !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Taren.lewis on 2014-03-03
```
uname -a
Linux ChrUbuntu 3.4.0 #1 SMP Sun Aug 26 19:17:55 EDT 2012 x86_64 x86_64 x86_64 GNU/Linux

lsb_release
Distributor ID:     Ubuntu
Description:     Ubuntu 12.04 LTS
Release:     12.04
Codename:     precise

lspci
01:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
     Subsystem: Foxconn International, Inc. Device [105b:e052]
     Kernel modules: ath9k_btcoex
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
     Subsystem: Acer Incorporated [ALI] Device [1025:0742]
     Kernel driver in use: tg3
--
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
     Subsystem: Acer Incorporated [ALI] Device [1025:0742]
     Kernel modules: sdhci-pci

lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai
Bus 001 Device 004: ID 064e:d251 Suyin Corp.
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd
Bus 002 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive

PCMCIA Card Info

iwconfig

rfkill

iw reg get
country 00:
     (2402 - 2472 @ 40), (3, 20)
     (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
     (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
     (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
     (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

lsmod
ath9k_btcoex          122426  0
mac80211              322190  1 ath9k_btcoex
ath9k_common_btcoex    12721  1 ath9k_btcoex
ath9k_hw_btcoex       336870  2 ath9k_btcoex,ath9k_common_btcoex
ath                    21066  3 ath9k_btcoex,ath9k_common_btcoex,ath9k_hw_btcoex
cfg80211              145311  3 ath9k_btcoex,mac80211,ath

nm-tool
NetworkManager Tool

State: disconnected

NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

interfaces
auto lo
iface lo inet loopback

iwlist

resolv.conf

blacklist
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

modinfo
filename:       /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k_btcoex/ath9k_btcoex.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
depends:        ath9k_hw_btcoex,mac80211,ath,ath9k_common_btcoex,cfg80211
intree:         Y
vermagic:       3.4.0 SMP mod_unload
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

filename:       /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k_btcoex/ath9k_common_btcoex.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
depends:        ath9k_hw_btcoex,ath
intree:         Y
vermagic:       3.4.0 SMP mod_unload

filename:       /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k_btcoex/ath9k_hw_btcoex.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
depends:        ath
intree:         Y
vermagic:       3.4.0 SMP mod_unload

filename:       /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
depends:        cfg80211
intree:         Y
vermagic:       3.4.0 SMP mod_unload

udev rules
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:03.0 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

dmesg
[    2.665018] Modules linked in: ath9k_common_btcoex ath9k_hw_btcoex snd_hda_intel snd_hda_codec ath snd_hwdep sdhci_pci(+) snd_pcm sdhci cfg80211 mmc_core tg3(+) nm10_gpio snd_timer snd_page_alloc
[    2.730703] ath9k 0000:01:00.0: request_irq failed
[    2.743515] Modules linked in: ath9k_btcoex(+) mac80211 ath9k_common_btcoex ath9k_hw_btcoex snd_hda_intel snd_hda_codec ath snd_hwdep sdhci_pci(+) snd_pcm sdhci cfg80211 mmc_core tg3(+) nm10_gpio snd_timer snd_page_alloc
[    2.781486]  [<ffffffffa01846ee>] ath_rate_control_unregister+0x599/0x809 [ath9k_btcoex]
[    2.812895]  [<ffffffffa0184981>] ath_pci_init+0x23/0x25 [ath9k_btcoex]
[    2.815602]  [<ffffffffa0194028>] init_module+0x28/0x1000 [ath9k_btcoex]
[    2.861211] ath9k: probe of 0000:01:00.0 failed with error -16

```

---

### Post by varunendra on 2014-03-03
I think a chromebook doesn't have something like a user accessible BIOS setup, does it? If yes try resetting it, although I've read more than once they don't allow access to the firmware/BIOS.

And please also post back the outputs of :
```
lsmod
grep [[:alnum:]] /sys/module/ath9*/parameters/*
```

Which country are you in? The driver seems to have picked up a default regulatory domain setting which can sometimes be a problem.
Can you try a Live DVD or USB of the latest Ubuntu LTS point release (12.04.4)?

**PS:**
It would be easier for you to post and for us to read if you post the whole output of the script in one block of code box. You can edit your above post to do so anytime you wish.
Posting it in multiple code boxes not only requires you to do more work, but also makes the post lengthier than it needs to be. :)

---

### Post by Taren.lewis on 2014-03-03
I live in the US. Could you provide me with a link to the LTS point release? I could USB it over and try to use it with instructions..Also, is my edit of the first post/code correct?

```
lsmod
Module                  Size  Used by
nls_iso8859_1          12352  1
nls_cp437              16448  1
vfat                   16448  1
fat                    46582  1 vfat
fuse                   63942  2
rfcomm                 25259  0
bluetooth             165173  9 rfcomm
memconsole             12352  0
joydev                 16448  0
ath9k_btcoex          122426  0
mac80211              322190  1 ath9k_btcoex
ath9k_common_btcoex    12721  1 ath9k_btcoex
ath9k_hw_btcoex       336870  2 ath9k_btcoex,ath9k_common_btcoex
snd_hda_intel          28736  0
snd_hda_codec          79858  1 snd_hda_intel
ath                    21066  3 ath9k_btcoex,ath9k_common_btcoex,ath9k_hw_btcoex
snd_hwdep              12390  1 snd_hda_codec
sdhci_pci              23569  1
snd_pcm                61370  2 snd_hda_intel,snd_hda_codec
sdhci                  25037  1 sdhci_pci
cfg80211              145311  3 ath9k_btcoex,mac80211,ath
mmc_core               75639  2 sdhci_pci,sdhci
tg3                   129257  1
nm10_gpio              12352  0
snd_timer              21094  1 snd_pcm
snd_page_alloc         12806  2 snd_hda_intel,snd_pcm


grep [[:alnum:]] /sys/module/ath9*/parameters/*
/sys/module/ath9k_btcoex/parameters/blink:0
/sys/module/ath9k_btcoex/parameters/btcoex_enable:1
/sys/module/ath9k_btcoex/parameters/nohwcrypt:0

```

Thanks again.

---

### Post by varunendra on 2014-03-03
> **Taren.lewis said:**
> I live in the US. Could you provide me with a link to the LTS point release? I could USB it over and try to use it with instructions..
Do not install it right away, just try it in live mode first. I'm not sure but I think we should be able to compile a more common driver from a newer kernel on your system, but a live session will confirm whether it would work or not. If the live session works flawlessly, you may choose to install the whole OS or only the driver from it.

Direct Download link and instructions for creating Live USB : [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

However, I highly recommend to use torrents for downloading. Higher download speed and guaranty of integrity of the downloaded ISO.
Torrent links : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

> Also, is my edit of the first post/code correct?
Yup, it is. :)

```

grep [[:alnum:]] /sys/module/ath9*/parameters/*
/sys/module/ath9k_btcoex/parameters/blink:0
/sys/module/ath9k_btcoex/parameters/btcoex_enable:1
/sys/module/ath9k_btcoex/parameters/nohwcrypt:0

```

The following maybe punches in the air, as the error message in 'dmesg' part indicates possible some other kind of problem, but trying won't hurt -

Please open try reloading the drivers with certain parameters -
```
sudo modprobe -rv ath9k_btcoex
sudo modprobe -v cfg80211 ieee80211_regdom=US
sudo modprobe -v ath9k_btcoex btcoex_enable=0 nohwcrypt=1
```
Watch out for errors and report back if there are any. These will be temporary changes that will be reset to defaults on next boot. So test the following without rebooting after running the codes.

If the above loaded fine, please check -
```
iw reg get
grep [[:alnum:]] /sys/module/ath9*/parameters/*
sudo iwlist scan
dmesg | grep ath9k | tail -20
```
Does the country code in the first command change from "00" to "US" ?
Do the values of parameters "btcoex_enable" and "nohwcrypt" change to 0 and 1 respectively ? (currently they are opposite)
Do you get any scan results (available networks)?
Any errors in the dmesg?

---

### Post by endlessinstant on 2014-03-03
Hi, 

which version of Ubuntu are you trying to install via chrubuntu? Several newer releases are a bit buggy, so it might be good to stick with precise at first.   

@varunendra The Acer C710 does not have a legacy boot mode so Taren.lewis will be forced working through the chrubuntu scripts to get Ubuntu bootable unless he wishes to flash the BIOS.  This is not a procedure I am familiar with so I don't wish to give specific advice on it but a google search will reveal several tutorials on the process.  

Taren.lewis, you may wish to look into crouton  

[https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)
[http://chromespot.com/2014/01/29/how-to-install-ubuntu-chromebook-crouton/](http://chromespot.com/2014/01/29/how-to-install-ubuntu-chromebook-crouton/)

Compared to chrUbuntu, crouton is more stable but less secure.  Your wireless should work out of the box because Chrome OS is still doing most of the work for you.

---

