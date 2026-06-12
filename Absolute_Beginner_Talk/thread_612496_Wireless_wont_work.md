---
title: "Wireless wont work"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-14
I just recently installed my Seirra WireLess AirCard 875 on my Ubuntu, everything went fine with the installation, and it will even show that it has connected online, the only thing is that immediately after connecting it gives me an error message and doesnt let me access the internet. Can someone breakdown a step by step installation process so I can reinstall it and make sure everything is right? And please no links, I installed using a link that someone gave me and thats why I think I ran into the errors because the link's instuctions were hard to follow.

---

### Post by SpiritIsReality on 2007-11-14
howdy
Can you give me the link and I'll see if I can help you.
trails

---

### Post by RobotoWorks on 2007-11-14
Oops, Im sorry I forgot the link, besides that can anyone help me?

---

### Post by RobotoWorks on 2007-11-14
Is there anyone that can help, that could talk through pm?

---

### Post by joslinar on 2007-11-14
What is the error message that you are getting?
Is the wifi light in the pc on?
What is the output if you type lspci in the command prompt?
What is the output if you type "sudo dmesg | grep -i net in the command prompt?

---

### Post by RobotoWorks on 2007-11-14
I get the error message "Failed to connect" the wifi light is on, when I typed in the first code nothing happened but for the second one heres what I got:

35.073388] NET: Registered protocol family 16
[   35.364095] NET: Registered protocol family 8
[   35.364098] NET: Registered protocol family 20
[   35.394720] NET: Registered protocol family 2
[   36.196438] audit: initializing netlink socket (disabled)
[   36.584646] NET: Registered protocol family 1
[    4.528000] r8169 Gigabit Ethernet driver 2.2LK loaded
[   14.944000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   15.080000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   20.380000] NET: Registered protocol family 31
[   76.196000] NET: Registered protocol family 10
[   76.196000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.200000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1156.684000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1159.208000] NET: Registered protocol family 17

---

### Post by SpiritIsReality on 2007-11-14
you can pm me
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+AirCard+875&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+AirCard+875&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=AirCard+875+install+site%3Aubuntuforums.org&as_qdr=y&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=AirCard+875+install+site%3Aubuntuforums.org&as_qdr=y&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+AirCard+875&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+AirCard+875&btnG=Search&meta=)

---

### Post by RobotoWorks on 2007-11-14
Thanks for the help, is the card guarrenteed to work?

---

### Post by joslinar on 2007-11-14
> **RobotoWorks said:**
> Thanks for the help, is the card guarrenteed to work?

I'm not sure what you mean with "guaranteed to work" but with open source and in fact, with anything in the real world there are no guarantees. 

I apologize for not telling you that the lspci command has to be preceded by sudo. Since the card appeared in the dmesg command we don't need it's output for now.

It seems that driver-wise your card is correctly installed and recognized by the kernel. You might want to reinstall the driver or if this doesn't work use the windows driver instead.

To remove the driver you will need to type ```
sudo modprobe -r xxxx
```
 where xxxx stands for the driver. If you don't know the driver or module name you will have to look for it by typing ```
sudo modprobe -l
``` and try to figure out the module from the list's output.

Once you have located the module you can reinstall it with ```
sudo modprobe xxxx
```

---

### Post by SpiritIsReality on 2007-11-14
joslinar ... thanks

---

### Post by RobotoWorks on 2007-11-14
> **joslinar said:**
> I'm not sure what you mean with "guaranteed to work" but with open source and in fact, with anything in the real world there are no guarantees. 

I apologize for not telling you that the lspci command has to be preceded by sudo. Since the card appeared in the dmesg command we don't need it's output for now.

It seems that driver-wise your card is correctly installed and recognized by the kernel. You might want to reinstall the driver or if this doesn't work use the windows driver instead.

To remove the driver you will need to type ```
sudo modprobe -r xxxx
```
 where xxxx stands for the driver. If you don't know the driver or module name you will have to look for it by typing ```
sudo modprobe -l
``` and try to figure out the module from the list's output.

Once you have located the module you can reinstall it with ```
sudo modprobe xxxx
```

Thanx but when I enter the code to retrieve my driver it gives me this:

/lib/modules/2.6.22-14-generic/ubuntu/misc/tifm/tifm_sd.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/tifm/ms_block.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/tifm/memstick.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/tifm/tifm_core.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/tifm/mspro_block.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/heci/heci.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/nozomi.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/gnbd.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/av5100.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/lmpcm_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/acerhk.ko
/lib/modules/2.6.22-14-generic/ubuntu/misc/pbe5.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/fsam7400.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/eeprom_93cx6.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/sd8686/sd8xxx.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/prism2_usb/prism2_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl8180/r8180.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54common.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/acx/acx.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p80211/p80211.ko
/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko
/lib/modules/2.6.22-14-generic/ubuntu/net/atl2/atl2.ko
/lib/modules/2.6.22-14-generic/ubuntu/net/et131x/et131x.ko
/lib/modules/2.6.22-14-generic/ubuntu/net/e1000-ich9/e1000-ich9.ko
/lib/modules/2.6.22-14-generic/ubuntu/net/ipg/ipg.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/quickcam/quickcam.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb/lirc_mceusb.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_sasem/lirc_sasem.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_cmdir/commandir.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_cmdir/lirc_cmdir.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_atiusb/lirc_atiusb.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_ttusbir/lirc_ttusbir.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_i2c/lirc_i2c.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_it87/lirc_it87.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_serial_igor/lirc_serial_igor.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_serial/lirc_serial.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_bt829/lirc_bt829.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_pvr150/lirc_pvr150.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_streamzap/lirc_streamzap.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_dev/lirc_dev.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_sir/lirc_sir.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2/lirc_mceusb2.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_imon/lirc_imon.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_igorplugusb/lirc_igorplugusb.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ov511/ov511_decomp.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ov511/ov511.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ov511/ov518_decomp.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/i2c-drivers/saa717x.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/ivtv/driver/ivtv-fb.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/isight/isight_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/acpi/tc1100-wmi.ko
/lib/modules/2.6.22-14-generic/ubuntu/acpi/sony_acpi.ko
/lib/modules/2.6.22-14-generic/ubuntu/acpi/pcc_acpi.ko
/lib/modules/2.6.22-14-generic/ubuntu/acpi/dev_acpi.ko
/lib/modules/2.6.22-14-generic/ubuntu/security/apparmor/apparmor.ko
/lib/modules/2.6.22-14-generic/ubuntu/fs/asfs/asfs.ko
/lib/modules/2.6.22-14-generic/ubuntu/fs/gfs/gfs.ko
/lib/modules/2.6.22-14-generic/ubuntu/fs/unionfs/unionfs.ko
/lib/modules/2.6.22-14-generic/ubuntu/fs/squashfs/squashfs.ko
/lib/modules/2.6.22-14-generic/volatile/ath_hal.ko
/lib/modules/2.6.22-14-generic/volatile/fcdsl.ko
/lib/modules/2.6.22-14-generic/volatile/fcdsl2.ko
/lib/modules/2.6.22-14-generic/volatile/fcdslsl.ko
/lib/modules/2.6.22-14-generic/volatile/fcdslslusb.ko
/lib/modules/2.6.22-14-generic/volatile/fcdslusb.ko
/lib/modules/2.6.22-14-generic/volatile/fcdslusb2.ko
/lib/modules/2.6.22-14-generic/volatile/fcdslusba.ko
/lib/modules/2.6.22-14-generic/volatile/fcpci.ko
/lib/modules/2.6.22-14-generic/volatile/fcusb.ko
/lib/modules/2.6.22-14-generic/volatile/fglrx.ko
/lib/modules/2.6.22-14-generic/volatile/fwlanusb.ko
/lib/modules/2.6.22-14-generic/volatile/fxusb.ko
/lib/modules/2.6.22-14-generic/volatile/nvidia.ko
/lib/modules/2.6.22-14-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.22-14-generic/volatile/nvidia_new.k

Then when I enter the driver number: 2.6.22 it gives me this:
FATAL: Module 2.6.22 not found.

So what did I do wrong and how can I fix it?

---

### Post by stchman on 2007-11-14
> **RobotoWorks said:**
> I just recently installed my Seirra WireLess AirCard 875 on my Ubuntu, everything went fine with the installation, and it will even show that it has connected online, the only thing is that immediately after connecting it gives me an error message and doesnt let me access the internet. Can someone breakdown a step by step installation process so I can reinstall it and make sure everything is right? And please no links, I installed using a link that someone gave me and thats why I think I ran into the errors because the link's instuctions were hard to follow.

Please post an lspci output here.  We need to know what chipset that wireless card uses.

---

### Post by SpiritIsReality on 2007-11-14
thankyou stchman iou

---

### Post by RobotoWorks on 2007-11-14
I can do that, but I need the code that will help me tell you.

---

### Post by RobotoWorks on 2007-11-14
Code please....

---

### Post by RobotoWorks on 2007-11-14
Bump....

---

### Post by FuturePilot on 2007-11-14
You mean
```
lspci
```
?

---

### Post by RobotoWorks on 2007-11-14
Thanks heres what it gave me:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d0300000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Memory at d0380000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0640000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: 0000000034000000-00000000340fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: d0100000-d01fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff10
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff10

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 20
        I/O ports at 2000 [size=256]
        Memory at d0000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 34000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

04:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at d0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

04:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0200800 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

04:06.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at d0200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

04:06.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0201000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

04:06.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at d0200900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

04:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at d0200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 3000 [size=128]
        Capabilities: [50] Power Management version 2

05:00.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Unknown device 18d7:0001
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at 38000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

05:00.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Unknown device 18d7:0001
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at 38001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

robotoworks@robotoworks-laptop:~$

---

### Post by stchman on 2007-11-15
> **RobotoWorks said:**
> Thanks heres what it gave me:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d0300000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Memory at d0380000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0640000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: 0000000034000000-00000000340fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: d0100000-d01fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff10
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff10

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 20
        I/O ports at 2000 [size=256]
        Memory at d0000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 34000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

04:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at d0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

04:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0200800 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

04:06.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at d0200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

04:06.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0201000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

04:06.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at d0200900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

04:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at d0200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 3000 [size=128]
        Capabilities: [50] Power Management version 2

05:00.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Unknown device 18d7:0001
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at 38000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

05:00.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Unknown device 18d7:0001
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at 38001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

robotoworks@robotoworks-laptop:~$

According to the lspci output your wireless card is an Intel 3945ABG all you need to do to get that card working is just enable the restricted driver.  Go to:

System--->Administration--->Restricted Drivers Manager and enable the driver.  Reboot and you should be good to go.

---

### Post by SpiritIsReality on 2007-11-15
> **FuturePilot said:**
> You mean
```
lspci
```
?tx

---

### Post by SpiritIsReality on 2007-11-15
howdy stchman 
sure good to see you.

---

