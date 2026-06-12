---
title: "Samsung N102SP Netbook Graphics, Resolution, Brightness Issues"
date: 2012-06-19
forum: Any Other OS
---

### Post by ernz on 2012-06-19
I have a Samsung N102SP Netbook running 12.04 (Mint 13). Everything is functional except for the correct resolution, brightness controls and external monitor functionality. Please help.

**Hotkeys**

The hot keys (apart from brightness) can be enabled with:

```
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samsung-tools samsung-backlight
sudo reboot
```

**Brightness**

The brightness up/down function keys do not work. They do absolutely nothing. There are two workarounds:

1) At the GRUB bootloader screen, tap down to disable the auto countdown and then the FN + UP/DOWN brightness controls will work and be remembered before you enter the OS.

2) Run 

```
sudo setpci -s 00:02.0 f4.b=ff
```

... for full brightness, or...

```
sudo setpci -s 00:02.0 f4.b=33
```

... for dimmed brightness. ff and 33 are hex values. 00 is black. ff is brightest....so, yea....don't use 00! (haha?)

**External Monitor - HELP?**

When an external monitor is plugged in, nothing happens. I see no screen controls pop up and the screen function key does nothing - the plugged in monitor just stays black. Help?

**Resolution**

The only resolution offered to me is 800x600 which is fugly. The max resolution offered when I boot into windows is 1024x600 which looks great. Ideally, I'd like to be able to use this 1024x600 screen resolution but I can't find any sane way of doing it that actually works! ARGH! 

Here is the chipset:

```
0:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Samsung Electronics Co Ltd Device c629
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at dfc00000 (32-bit, non-prefetchable) [size=1M]
        I/O ports at f100 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
```

And here is the lspci output:

 ```
   user@MintNetbook ~ $ lspci
    00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
    00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
    00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
    00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
    00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
    00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    01:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
    02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```


This is driving me insane, because everything else works so well. Please help me figure this out so other people can find a quick fix too? Thanks!

Edit: I tried xubuntu and mint - exact same problems on both variants.

---

### Post by ernz on 2012-06-22
Bump

---

### Post by dingody on 2012-08-07
hi&#65292;ernz,i have the same problem .Samsuang N102sp uses the intel gma 3600 and it just supported windows7.recently ,2012-7-8,the xp driver just came out.
([http://drivers.mydrivers.com/search-101-490/h57382-0-3-1-0-1.htm](http://drivers.mydrivers.com/search-101-490/h57382-0-3-1-0-1.htm))
i don't think linux driver will be programmed.but i found a web page.([http://www.intel.com/support/graphics/intelgma3600/sb/cs-033597.htm](http://www.intel.com/support/graphics/intelgma3600/sb/cs-033597.htm))
is that a meego driver?i m not sure.since meego is also a kind of linux ,maybe it will help&#12290; 

if you got any good news ,please tell me ,(dingody#163.com)
thanks~

---

