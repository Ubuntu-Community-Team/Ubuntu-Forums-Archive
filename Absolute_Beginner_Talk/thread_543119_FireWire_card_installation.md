---
title: "FireWire card installation"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by koosfoto.hu on 2007-09-04
Hi!

I plugged in my FireWire card. And nothing happened!

I connected a Sony mini DV camera to it now. And I would like to read in videos and edit it under the Ubuntu.
My system does not say a word about the card.

In Kino there is nothing under the IEEE 1394 tab. No device is listed there.

What to do?
How can I make it recognized by the system and make it usable for video input?

I am new to Ubuntu, and my knowledge is rather shaky in it. Please, explaine it to me slowly, if possible. I know how to start the Konsole... and not much more about it.

Thanks a lot!

Tamas

---

### Post by por100pre1 on 2007-09-04
To see if it is detected:

```
lspci
```

and look for something like: FireWire (IEEE 1394)...

---

### Post by koosfoto.hu on 2007-09-04
Hi por100pre1!

I am affraid, NOT:

 lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0b.0 SCSI storage controller: Adaptec AIC-7892A U160/m (rev 02)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:0e.0 USB Controller: NEC Corporation USB (rev 41)
00:0e.1 USB Controller: NEC Corporation USB (rev 41)
00:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)


Thanks,

Tamas

---

### Post by koosfoto.hu on 2007-09-05
Hi por100pre1!

Thanks for the idea... I changed slot... and now it is HERE:

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev
 c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AG                              P]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40                              )
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/                              C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                               (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                               (rev 16)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio                               Controller (rev 50)
00:09.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
00:0b.0 SCSI storage controller: Adaptec AIC-7892A U160/m (rev 02)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev                               08)
00:0e.0 USB Controller: NEC Corporation USB (rev 41)
00:0e.1 USB Controller: NEC Corporation USB (rev 41)
00:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP                               8x] (rev a2)


What to do now?

Thanks,

Tamas

---

### Post by por100pre1 on 2007-09-05
Check if [this]("https://help.ubuntu.com/community/Firewire") helps you.

---

### Post by koosfoto.hu on 2007-09-05
Hi!

Under /dev there is dv1394 and under it there is a file, called 0.

When I start Kino 0.9.2 - no message is displayed at Capture.
In the IEEE 1394 in preferences contains NO device.
There is  /dev/raw1394 in the dv1394 device field.

Here I am stopped... and lost. 
How to go further?

Thanks, again!

Tamas

---

### Post by por100pre1 on 2007-09-05
Did you try using:

```
sudo modprobe dv1394
```

and then selecting /dev/dv1394/0 as explained [here]("https://help.ubuntu.com/community/Firewire#head-8df38ebe9c629c12e4da90fb24f3a81ca91accf0")?

I'm just guessing... :-k

---

### Post by koosfoto.hu on 2007-09-05
Yes, I did.
And there is NO warning (what should be), and there is nothing in the list.
:-(

Any further ide for continuing?

Greetings,

Tamas

---

