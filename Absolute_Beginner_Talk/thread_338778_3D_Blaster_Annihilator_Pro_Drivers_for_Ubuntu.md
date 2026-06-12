---
title: "3D Blaster Annihilator Pro Drivers for Ubuntu?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by barbarella on 2007-01-14
Disclaimer:
I already ran a very facile search, here. No luck, so I post:

What drivers do I use for my old videocard?
I've gone to nvidia's web site ([http://www.nvidia.com/content/drivers/drivers.asp)](http://www.nvidia.com/content/drivers/drivers.asp)). 
Here's what seems likely, let me know.
Linux IA32
Free BSD

Clue a paranoid android in?
Much appreciated!

---

### Post by po0f on 2007-01-14
barbarella,

What does `lspci` say your card is?  I haven't heard of it, it might require installing [nvidia-glx-legacy](http://packages.ubuntu.com/edgy/misc/nvidia-glx-legacy) instead of the newer [nvidia-glx](http://packages.ubuntu.com/edgy/x11/nvidia-glx) driver.

[EDIT]

Run the `lspci` command from a terminal and post the output if you would.

---

### Post by crispy_420 on 2007-01-15
It may that you'll just have to go with just the generic vesa driver. You won't get 3D acceleration but it will work. And good could card even render 3d accel. if nvidia doesn't supply drivers.

---

### Post by barbarella on 2007-01-19
Here it is...

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 02)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
00:0b.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 01)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
01:00.0 VGA compatible controller: nVidia Corporation NV10DDR [GeForce 256 DDR] (rev 10)

What do you think?

---

### Post by dando80 on 2007-03-22
I think that geforce 256 nv10 chipset should be supported by the standard nvidia driver and not the nvidia legacy.

---

