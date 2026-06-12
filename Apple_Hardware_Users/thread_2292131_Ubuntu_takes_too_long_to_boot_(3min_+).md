---
title: "Ubuntu takes too long to boot (3min +)"
date: 2015-08-25
forum: Apple Hardware Users
---

### Post by jdsampayo on 2015-08-25
Hello,

I have a MacBookPro with 3.19.0-18-generic 18-Ubuntu x86_64 x86_64 x86_64 GNU/Linux

The laptop is taking too long to boot, here it is the output of systemd-analyze blame:

```

jdsampayo@jdsampayo-MacBookPro:~$ 
      3min 246ms systemd-udev-settle.service
          8.102s dev-disk-by\x2duuid-bcd09300\x2ddb58\x2d4451\x2dad61\x2d022a484
          7.895s postgresql@9.4-main.service
          7.354s gpu-manager.service
          6.791s NetworkManager-wait-online.service
          4.639s plymouth-quit-wait.service
          4.553s ufw.service
          3.787s systemd-udevd.service
          2.753s NetworkManager.service
          2.567s wicd.service
          1.943s accounts-daemon.service
          1.897s ModemManager.service
          1.860s systemd-modules-load.service
          1.742s thermald.service
          1.641s systemd-tmpfiles-setup-dev.service
          1.110s grub-common.service
          1.021s dev-sda5.swap
           903ms systemd-journald.service
           797ms avahi-daemon.service
           494ms irqbalance.service
           446ms systemd-sysctl.service
           384ms lm-sensors.service
           353ms systemd-setup-dgram-qlen.service

```

And the output of dmesg around the time it takes most:

```

[   13.434401] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   13.434403] [drm] Driver supports precise vblank timestamp query.
[   13.434478] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.459169] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[   13.459397] acpi device:10: registered as cooling_device4
[   13.459452] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   13.459506] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[   13.530350] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   13.547331] fbcon: inteldrmfb (fb0) is primary device
[   13.547352] Console: switching to colour frame buffer device 160x50
[   13.547368] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   13.547369] i915 0000:00:02.0: registered panic notifier
[   13.623557] applesmc: key=380 fan=1 temp=24 index=23 acc=1 lux=2 kbd=1
[   13.693179] input: applesmc as /devices/platform/applesmc.768/input/input8
[   14.324688] cfg80211: Calling CRDA to update world regulatory domain
[   14.326315] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   14.367565] AVX version of gcm_enc/dec engaged.
[   14.367568] AES CTR mode by8 optimization enabled
[   14.390089] sound hdaudioC0D0: autoconfig: line_outs=2 (0xb/0xa/0x0/0x0/0x0) type:speaker
[   14.390092] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.390094] sound hdaudioC0D0:    hp_outs=1 (0x9/0x0/0x0/0x0/0x0)
[   14.390095] sound hdaudioC0D0:    mono: mono_out=0x0
[   14.390096] sound hdaudioC0D0:    dig-out=0x10/0x0
[   14.390097] sound hdaudioC0D0:    inputs:
[   14.390099] sound hdaudioC0D0:      Mic=0xd
[   14.390100] sound hdaudioC0D0:      Line=0xc
[   14.457679] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.457732] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.457776] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   14.457818] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.457858] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   14.571527] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   14.571921] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   14.571935] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2059, Revision 0, Version 1
[   14.571936] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[   14.572444] Broadcom 43xx driver loaded [ Features: PNL ]
[   15.320653] cfg80211: World regulatory domain updated:
[   15.320656] cfg80211:  DFS Master region: unset
[   15.320657] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   15.320659] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.320660] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.320662] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.320663] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.320664] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.419825] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.460884] Bluetooth: Core ver 2.20
[   15.460898] NET: Registered protocol family 31
[   15.460899] Bluetooth: HCI device and connection manager initialized
[   15.460903] Bluetooth: HCI socket layer initialized
[   15.460906] Bluetooth: L2CAP socket layer initialized
[   15.460912] Bluetooth: SCO socket layer initialized
[   15.586296] input: bcm5974 as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.2/input/input14
[   15.586369] usbcore: registered new interface driver bcm5974
[   15.596178] usbcore: registered new interface driver btusb
[   15.607392] usb 1-1.1.1: USB disconnect, device number 6
[   15.746115] intel_rapl: Found RAPL domain package
[   15.746118] intel_rapl: Found RAPL domain core
[   15.746119] intel_rapl: Found RAPL domain uncore
[   15.753822] media: Linux media interface: v0.10
[   15.763632] input: Apple Computer, Inc. IR Receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/0003:05AC:8242.0001/input/input15
[   15.792769] b43 bcma0:1 wlan1: renamed from wlan0
[   15.817731] appleir 0003:05AC:8242.0001: input,hiddev0,hidraw1: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.7-1.1/input0
[   15.865936] usb 1-1.1.2: USB disconnect, device number 7
[   15.866687] Linux video capture interface: v2.00
[   16.133915] Adding 2115580k swap on /dev/sda5.  Priority:-1 extents:1 across:2115580k FS
[   16.485049] uvcvideo: Found UVC 1.00 device FaceTime HD Camera (Built-in) (05ac:8509)
[   16.491924] input: FaceTime HD Camera (Built-in) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input16
[   16.491981] usbcore: registered new interface driver uvcvideo
[   16.491982] USB Video Class driver (1.1.1)
[  187.538939] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[  187.559780] systemd-journald[242]: Received request to flush runtime journal from PID 1
[  188.091769] audit: type=1400 audit(1440511663.959:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=698 comm="apparmor_parser"
[  188.091781] audit: type=1400 audit(1440511663.959:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=698 comm="apparmor_parser"
[  188.093326] audit: type=1400 audit(1440511663.959:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=698 comm="apparmor_parser"
[  188.093331] audit: type=1400 audit(1440511663.959:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=698 comm="apparmor_parser"
[  188.093334] audit: type=1400 audit(1440511663.959:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=698 comm="apparmor_parser"
[  188.093338] audit: type=1400 audit(1440511663.959:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=698 comm="apparmor_parser"
[  188.100695] audit: type=1400 audit(1440511663.967:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=698 comm="apparmor_parser"
[  188.100702] audit: type=1400 audit(1440511663.967:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=698 comm="apparmor_parser"
[  188.100706] audit: type=1400 audit(1440511663.967:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=698 comm="apparmor_parser"
[  188.100709] audit: type=1400 audit(1440511663.967:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=698 comm="apparmor_parser"
[  188.709245] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  188.709248] Bluetooth: BNEP filters: protocol multicast
[  188.709253] Bluetooth: BNEP socket layer initialized
[  188.712881] Bluetooth: RFCOMM TTY layer initialized
[  188.712887] Bluetooth: RFCOMM socket layer initialized
[  188.712891] Bluetooth: RFCOMM ver 1.11
[  192.397589] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  194.048607] wlan1: authenticate with 78:71:9c:c3:f3:90
[  194.069260] wlan1: send auth to 78:71:9c:c3:f3:90 (try 1/3)
[  194.070814] wlan1: authenticated
[  194.073069] wlan1: associate with 78:71:9c:c3:f3:90 (try 1/3)
[  194.082861] wlan1: RX AssocResp from 78:71:9c:c3:f3:90 (capab=0xc11 status=0 aid=1)
[  194.083269] wlan1: associated
[  194.083306] cfg80211: Calling CRDA for country: US
[  194.084894] cfg80211: Regulatory domain changed to country: US
[  194.084897] cfg80211:  DFS Master region: FCC
[  194.084898] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  194.084900] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)


```

Does anybody have a suggestion?

Thanks!

---

### Post by PaulW2U on 2015-08-25
*Thread moved to **Apple Hardware Users**.*

---

### Post by ajgreeny on 2015-08-25
```
[   16.485049] uvcvideo: Found UVC 1.00 device FaceTime HD Camera (Built-in) (05ac:8509)
[   16.491924] input: FaceTime HD Camera (Built-in) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input16
[   16.491981] usbcore: registered new interface driver uvcvideo
[   16.491982] USB Video Class driver (1.1.1)
[  187.538939] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
```
It appears that the problem is the loading of the driver for the webcam of your machine that is causing the very long delay; it takes 3m51s to load.

Unfortunately I have no knowledge of anything apple/mac but it may be worth your searching for any known bugs for use of that machine and the webcam it uses.

---

