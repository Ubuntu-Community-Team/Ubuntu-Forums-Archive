---
title: "Macbook 2015 (8,1) SPI Keyboard not detected with Kernel 4.2rc6"
date: 2015-08-14
forum: Apple Hardware Users
---

### Post by denverthedragon on 2015-08-14
Latest changes to [hid_apple]("https://bugzilla.kernel.org/show_bug.cgi?id=96771") include support for the usb keyboard and touchpad on the macbook pro. 
When Macbook Pro owners run lsusb, they get the keyboard and trackpad in the list. 05ac:0272  (or 0273 depending on layout). 

On the Macbook, the device does not appear in lsusb because it is connected via SPI... In OSX, it appears under the SPI section. i.e. in System Information > Hardware > SPI > Apple Internal Keyboard / Trackpad.   But (encouragingly) it has the same product & vendor id. 

So I thought the first thing to do is try and at least get to a point where I can see the keyboard/touchpad device in a list in Linux...

Running lspci on the macbook I get:
```

00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:15.0 DMA controller: Intel Corporation Wildcat Point-LP Serial IO DMA Controller (rev 03)
00:15.2 Serial bus controller [0c80]: Intel Corporation Wildcat Point-LP Serial IO I2C Controller #1 (rev 03)
00:15.4 Serial bus controller [0c80]: Intel Corporation Wildcat Point-LP Serial IO GSPI Controller #1 (rev 03)
00:15.5 Serial controller: Intel Corporation Wildcat Point-LP Serial IO UART Controller #0 (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation Device 43a3 (rev 05)
02:00.0 Multimedia controller: Broadcom Corporation 720p FaceTime HD Camera
03:00.0 *** the NVME controller should be here but the file got truncated.  ***

```

So it looked to me (after some googling) like the SPI drivers for the Wildcat are in i2c_i801...

If I [FONT=system]modprobe i2c_i801[/FONT] I get a warning telling me :
```
[  445.297196] ACPI Warning: SystemIO range 0x000000000000EFA0-0x000000000000EFBF conflicts with OpRegion 0x000000000000EFA0-0x000000000000EFAF (\_SB_.PCI0.SBUS.SMBI) (20150619/utaddress-254)
[  445.297210] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

So, reboot and set [FONT=system]acpi=off[/FONT] in grub. Then i get:
```

[   70.020206] i801_smbus 0000:00:1f.3: can't find IRQ for PCI INT C; please try using pci=biosirq
[   70.020214] ACPI Exception: AE_BAD_PARAMETER, Thread 835532544 could not acquire Mutex [0x1] (20150619/utmutex-285)
[   70.020231] genirq: Flags mismatch irq 0. 00000080 (i801_smbus) vs. 00015a00 (timer)
[   70.020233] i801_smbus 0000:00:1f.3: Failed to allocate irq 0: -16
[   70.020235] i801_smbus 0000:00:1f.3: SMBus using polling

```

So I set [FONT=system]acpi=off pci=biosirq[/FONT], modprobe again and get:
```

[  111.248202] i801_smbus 0000:00:1f.3: can't find IRQ for PCI INT C; please try using pci=biosirq
[  111.248210] ACPI Exception: AE_BAD_PARAMETER, Thread 1301602368 could not acquire Mutex [0x1] (20150619/utmutex-285)
[  111.248226] genirq: Flags mismatch irq 0. 00000080 (i801_smbus) vs. 00015a00 (timer)
[  111.248228] i801_smbus 0000:00:1f.3: Failed to allocate irq 0: -16
[  111.248230] i801_smbus 0000:00:1f.3: SMBus using polling

```

After all this /sys/bus/spi/devices still lists nothing. 

Am I along the right lines or way off track? Does anyone have anymore information about SPI / all the Wildcat devices?

AND... how is it that the keyboard works in grub? (grub also can read off the internal NVME drive, but that's covered in other posts)

( Note: I can't get the NVME disk to work, but that's covered in other threads, I'm booting off a USB drive on a hub into Ubuntu 15.10 running Kernel 4.2rc6 )

---

### Post by john-morton on 2015-09-17
[COLOR=#333333]Just a quick update... As far as I can tell (which is not to confirm either way or the other) - after having just installed kernel 4.3RC1 (admittedly on my Ubuntu-based system); there doesn't appear to have been any changes which have enabled the track-pad, keyboard or visibility of the disk. You may want to try this yourself within your own environment but it's still looking like this is a fringe use-case and not getting any attention.[/COLOR]

---

### Post by john-morton on 2015-09-28
You guys might be interested in the following: [https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook?p=2729857#post2729857](https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook?p=2729857#post2729857)

Cheers,

John

---

### Post by john-morton on 2015-11-17
[http://moepi.net/?page_id=213](http://moepi.net/?page_id=213)

[https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook?p=2738165#post2738165](https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook?p=2738165#post2738165)

---

