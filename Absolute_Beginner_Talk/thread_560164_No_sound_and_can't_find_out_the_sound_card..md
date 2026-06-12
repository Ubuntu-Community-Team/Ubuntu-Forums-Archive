---
title: "No sound and can't find out the sound card."
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-09-26
I have tried all the helps and guidelines to get my sound. it worked before and now when i installd fiesty from edgy i have no sound and cant find sound card i have.

 I am using a HP M70.

" alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
root@hackBOX:/home/phizikal# lshw -C multimedia
root@hackBOX:/home/phizikal# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 Communication controller: Agere Systems LT WinModem
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
"

---

### Post by overdrank on 2007-09-26
Hi is it disabled somehow in bios?

---

### Post by phizikal on 2007-09-26
How can I find out?

---

### Post by overdrank on 2007-09-26
> **phizikal said:**
> How can I find out?

You will have to enter bios on the the system. You can do that by entering a certain key, it could be delete key or the F12 key. I cant remember what the typical for the HP systems but is should tell you when the system boots and you may have to use the esc key.

---

### Post by alienexplorers on 2007-09-26
Reboot your computer and when it starts to load the bios routine hit (del, F1) or what ever key gets you into the BIOS.  Look threw your BIOS to see if anything mentions Audio or Sound.

---

