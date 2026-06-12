---
title: "video card with tv tuner"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-10-10
how would i cheack to see if my video cards tv tuner is detected by ubuntu?

in my searching i've found some.
for:
```
$ lspci | grep -i bt
```
returns: nothing

for:
```
$ lspci|grep media
```
returns:
```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```
```


for:
$ xawtv -hwscan
```
returns:```
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
looking for available devices
port 57-57
    type : Xvideo, image scaler
    name : NV Video Overlay

port 58-89
    type : Xvideo, image scaler
    name : NV Video Blitter

```

Is there anything else?  Or is it conclusive that my tv tuner function will never* be functionable in ubuntu?


*never:near future

---

### Post by anaconda on 2006-10-10
What card is it? Maker, model..??

Have you looked at:
[www.linuxtv.org](www.linuxtv.org)

Maybe you just need firmware (driver) for it

---

### Post by insub2 on 2006-10-10
i have a Chaintech nVIDIA GeForce FX5600/XT  A-FM6N.  here is the [manufacturers page]("http://www.chaintechusa.com/tw/eng/product_spec.asp?MPSNo=14&PISNo=197").

i've been to that site but it have no idea how to navigate it and what i'm looking for.

thank you for your help.

---

### Post by Marsolin on 2006-10-10
Try installing [HAL Device Manager]("http://linuxappfinder.com/package/hal-device-manager"). It's a good tool for listing your detected hardware.

[XawTV]("http://linuxappfinder.com/package/xawtv") might be listing the device you are looking for anyway. It's hard to tell what it should say though.

---

### Post by insub2 on 2006-10-10
> **Marsolin said:**
> Try installing [HAL Device Manager]("http://linuxappfinder.com/package/hal-device-manager"). It's a good tool for listing your detected hardware.

[XawTV]("http://linuxappfinder.com/package/xawtv") might be listing the device you are looking for anyway. It's hard to tell what it should say though.


HAL was already installed.  what am i suppose to do with it?

what do you want to know?  what am i looking for?

---

### Post by Marsolin on 2006-10-10
> **insub2 said:**
> HAL was already installed.  what am i suppose to do with it?

what do you want to know?  what am i looking for?

There should be a Device Manager entry in the System menu if it is installed. Run it and scroll down through the devices to see if one sounds like your card. I don't have that card so I don't know what it should be listed as.

---

### Post by fstab on 2006-10-11
My tuner card shows up in dmesg.  I grep for tv or tuner to find it:
```

sh-3.1$ dmesg | grep -i tv
[17179592.832000] CORE cx88[0]: subsystem: 1002:00f9, board: ATI TV Wonder Pro [card=4,insmod option]
[17179592.832000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179593.068000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
```

```
sh-3.1$ dmesg | grep -i tuner
[17179592.832000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179593.068000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179593.068000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179593.068000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
```

```
sh-3.1$ dmesg | grep -A 25 -i "Linux video capture"
[17179592.700000] Linux video capture interface: v1.00
[17179592.768000] ts: Compaq touchscreen protocol output
[17179592.832000] cx2388x v4l2 driver version 0.0.5 loaded
[17179592.832000] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179592.832000] CORE cx88[0]: subsystem: 1002:00f9, board: ATI TV Wonder Pro [card=4,insmod option]
[17179592.832000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179592.944000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[17179592.944000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179592.956000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179593.044000] cx88[0]/0: found at 0000:01:02.0, rev: 5, irq: 209, latency: 64, mmio: 0xfd000000
[17179593.068000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179593.068000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179593.068000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[17179593.120000] cx88[0]/0: registered device video0 [v4l2]
[17179593.120000] cx88[0]/0: registered device vbi0
```

---

### Post by insub2 on 2006-10-11
for the HAL Device Maneger, see the attatchments.


as for the others:
```
insub2@AWESOME:~$ dmesg | grep -i tv
[17179590.112000] bttv: driver version 0.9.16 loaded
[17179590.112000] bttv: using 8 buffers with 2080k (520 pages) each for capture
```
```
insub2@AWESOME:~$ dmesg | grep -i tuner
```
```
insub2@AWESOME:~$ dmesg | grep -A 25 -i "Linux video capture"
[17179590.072000] Linux video capture interface: v1.00
[17179590.112000] bttv: driver version 0.9.16 loaded
[17179590.112000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179590.160000] Adding 1052216k swap on /dev/sda1.  Priority:-1 extents:1 across:1052216k
[17179590.272000] EXT3 FS on sda2, internal journal
[17179590.424000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179590.424000] md: bitmap version 4.39
[17179590.896000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179590.908000] NET: Registered protocol family 17
[17179593.028000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17179593.028000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179593.028000] ide: failed opcode was: unknown
[17179593.028000] end_request: I/O error, dev hdc, sector 12438656
[17179594.916000] cdrom: open failed.
[17179595.256000] kjournald starting.  Commit interval 5 seconds
[17179595.256000] EXT3 FS on sda3, internal journal
[17179595.256000] EXT3-fs: mounted filesystem with ordered data mode.
[17179599.840000] ACPI: Power Button (FF) [PWRF]
[17179599.840000] ACPI: Power Button (CM) [PWRB]
[17179599.840000] ACPI: Sleep Button (CM) [SLPB]
[17179599.952000] ibm_acpi: ec object not found
[17179599.988000] pcc_acpi: loading...
[17179604.620000] ppdev: user-space parallel port driver
[17179604.964000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179604.964000] apm: overridden by ACPI.
[17179610.424000] Bluetooth: Core ver 2.8
```

---

### Post by insub2 on 2006-10-11
so, should i give up?

---

