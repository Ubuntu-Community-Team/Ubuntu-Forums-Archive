---
title: "iBook G3 Original Airport Wireless"
date: 2006-09-25
forum: Apple PPC Users
---

### Post by krasi on 2006-09-25
I know this has been posted before but i didn't wanna clutter up other posts with this rambling.  I have an iBook G3 with an original Apple Airport Card(802.11 a/b). 

-----I will put all the debug and driver information below this.-----
 
I have installed the Gnome network manager and I don't get any prompts for WPA or any network connections in my taskbar at the top of the screen.  
Now one thing i did notice is under Networking I can see a wireless card and it is set to eth1.  my ethernet connection is set to eth0 and it works fine.  Now if i tried and use the gnome network manager i can enter in my info but it never connects successfully.  I can only enter a wep key not a WPA key. I can open up a web browser and click on a link and it goes nowhere.  It just sits then and ends up timing out after so many seconds.  Now that showed me that my card is installed and recognize but i can't use WPA to authenticate.  Also using DHCP gets an immediate failed to load page but using static gives me the hanging connection.
I tried using wi-fi radar but i couldn't find the specific driver I needed. I guess since my acrd is already installed. It will not pull a IP address.  i even tried using a static IP to no avail. 
  
Now i tried following the Ubuntu guide on the wiki page for wifi Docs but that didn't help.  I edited the wpa_supplicant.conf file with my network info but when i went into the file it was blank.  so i added and tried and still nothing.  I went through the drivers list and none of them matched what I had on my computer.  I must have an odd ball card.

I tried installing the WPAgui and it failed on install saying specific permissions on the package were denied even though i downloaded the package directly from Ubuntu website.  So that didn't work either.

Now here is all the debug information i could gather.


Driver listed using sudo wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf in terminal:

```
drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver
```

here is the output from iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Big Inhale"  Nickname:"Big Inhale"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Here is what is under /etc/network/interfaces:

```
iface eth0 inet static
address 10.0.1.13
netmask 255.0.0.0
gateway 10.0.1.1

auto eth1
iface eth1 inet dhcp
wireless-essid Big Inhale
wireless-key s:*************

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
```

Here is what I got from $iwlist eth scan:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Big Inhale"  Nickname:"Big Inhale"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.




eth1      Scan completed :
          Cell 01 - Address: 00:11:24:1F:6A:FB
                    ESSID:"Big Inhale"
                    Mode:Master
                    Frequency=2.412 GHz (Channel 1)
                    Signal level:-45 dBm  Noise level:-97 dBm
                    Encryption key:on
```

Here is the output from dmesg:

```
[   51.498654] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:c5:c8:86
[   51.498670] eth0: Found BCM5221 PHY
[   53.751145] input: PowerMac Beep as /class/input/input4
[   54.022528] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   54.031222] airport 0.15rc3 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   54.032317] airport: Physical address 80030000
[   55.234257] eth1: Hardware identity 0005:0001:0001:0002
[   55.234373] eth1: Station identity  001f:0001:0008:0046
[   55.234383] eth1: Firmware determined as Lucent/Agere 8.70
[   55.234390] eth1: Ad-hoc demo mode supported
[   55.234395] eth1: IEEE standard IBSS ad-hoc mode supported
[   55.234401] eth1: WEP supported, 104-bit key
[   55.234475] eth1: MAC address 00:30:65:21:D2:D9
[   55.234560] eth1: Station name "HERMES I"
[   55.234990] eth1: ready
[   55.236454] airport: Card registered for interface eth1
[   55.346317] apm_emu: APM Emulation 0.5 initialized.
[   55.585619] SCSI subsystem initialized
[   55.652263] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   55.652282] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   55.652289] ieee1394: sbp2: Try serialize_io=0 for better performance
[   56.067903] Adding 340980k swap on /dev/hda12.  Priority:-1 extents:1 across:340980k
[   56.340623] EXT3 FS on hda11, internal journal
[   56.918015] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   56.918033] md: bitmap version 4.39
[   56.948393] NET: Registered protocol family 17
[   58.225513] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   59.715769] cdrom: open failed.
[   64.860499] ieee80211_crypt: registered algorithm 'NULL'
[   64.867511] ieee80211: 802.11 data/management/control stack, git-1.1.7
[   64.867530] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   81.113903] [drm] Initialized drm 1.0.1 20051102
[   81.165228] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[   83.035861] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode
[   83.035889] agpgart: Putting AGP V2 device at 0000:00:10.0 into 1x mode
[   83.263498] [drm] Setting GART location based on old memory map
[   83.263600] [drm] writeback test succeeded in 1 usecs
[   83.633207] lp: driver loaded but no devices found
[   83.848028] ppdev: user-space parallel port driver
[   89.668784] Bluetooth: Core ver 2.8
[   89.668808] NET: Registered protocol family 31
[   89.668814] Bluetooth: HCI device and connection manager initialized
[   89.668847] Bluetooth: HCI socket layer initialized
[   89.814927] Bluetooth: L2CAP ver 2.8
[   89.814945] Bluetooth: L2CAP socket layer initialized
[   89.854719] Bluetooth: RFCOMM socket layer initialized
[   89.854787] Bluetooth: RFCOMM TTY layer initialized
[   89.854795] Bluetooth: RFCOMM ver 1.7
[  113.237515] NET: Registered protocol family 10
[  113.237937] lo: Disabled Privacy Extensions
[  113.238181] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  113.238194] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  113.238309] IPv6 over IPv4 tunneling driver

```

its looking more like I can't get my Airport Extreme base Station to be recognize as an access point.  I even tried through static and it still will not pick it up.  maybe that is my problem.  its not the laptop its look ore like the base station.

Please any and all help is appreciated.  I have been trying to figure this out through these forumns and many other aplces but cannot get it to owkr.  Thanks in advance.

---

### Post by bluesphere on 2006-09-26
Thought this might help

[http://www.ubuntuforums.org/showthread.php?t=246998&highlight=wpa+ppc](http://www.ubuntuforums.org/showthread.php?t=246998&highlight=wpa+ppc)

Sorry just realized PPC vs Intel. I'll keep a lookout for you

---

### Post by bluesphere on 2006-09-26
All right read through this. It looks to be in your neighborhood.

[http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa+ppc](http://www.ubuntuforums.org/showthread.php?t=230431&highlight=wpa+ppc)

---

### Post by krasi on 2006-09-26
i offically give up on getting wi-fi to work.  This takes to much time.  i will deal with wired until ubuntu decides to include WPA in their next releaseI(f ever) or an easier way to set it up.  This should not be this hard to get wi-fi running.  thanks for all your help everyone.

---

### Post by AlphaMack on 2006-09-27
WPA is a no-go right now.  You could get by with WEP.

---

### Post by eyeballer786 on 2007-10-28
How could I get it going with WEP?

---

