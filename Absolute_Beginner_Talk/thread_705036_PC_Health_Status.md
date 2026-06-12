---
title: "PC Health Status"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-02-22
you know how when you boot into BIOS, you can see your PC health status (CPU temp, clock speed, etc.)? is there an application for ubuntu that will allow me to view these stats without booting into the BIOS everytime?

---

### Post by PeterJS on 2008-02-22
You've got a couple of options. [Conky](http://conky.sf.net/) is in the [repositories](apt://conky) is pretty popular these days. If you're looking to go more old school you might look in to [Gkrellm](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html) which is also in the [repositories](apt://gkrellm)

---

### Post by ryanhaigh on 2008-02-22
I use lm-sensors and an applet in my gnome-panel
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by dcstar on 2008-02-23
> **Sinkingships7 said:**
> you know how when you boot into BIOS, you can see your PC health status (CPU temp, clock speed, etc.)? is there an application for ubuntu that will allow me to view these stats without booting into the BIOS everytime?

Please note that if you run a "Brisbane" core Athlon X2 the CPU diode temps are way off - I have to add 20C to them to get anything close to reality.

---

### Post by uhappo on 2008-02-23
> **ryanhaigh said:**
> I use lm-sensors and an applet in my gnome-panel
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Yeah, I got this working right now. A good one.

---

### Post by mgranet on 2008-02-23
> **dcstar said:**
> Please note that if you run a "Brisbane" core Athlon X2 the CPU diode temps are way off - I have to add 20C to them to get anything close to reality.

What about the Toledo's? I'm running the same cooler that came with my XP2100, and lm-sensors reports:

matt@linkub710:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +29°C
Core1 Temp:
             +29°C

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.39 V  (min =  +0.00 V, max =  +2.04 V)
in1:       +8.71 V  (min =  +0.00 V, max = +13.46 V)
AVCC:      +3.23 V  (min =  +0.00 V, max =  +4.08 V)
3VCC:      +3.23 V  (min =  +0.00 V, max =  +4.08 V)
in4:       +1.60 V  (min =  +0.00 V, max =  +2.04 V)
in5:       +1.82 V  (min =  +2.04 V, max =  +1.78 V) ALARM
in6:       +5.86 V  (min =  +6.27 V, max =  +6.53 V) ALARM
VSB:       +3.18 V  (min =  +0.00 V, max =  +4.08 V)
VBAT:      +1.81 V  (min =  +0.00 V, max =  +4.08 V)
in9:       +1.54 V  (min =  +2.01 V, max =  +1.53 V) ALARM
Case Fan: 2518 RPM  (min =    0 RPM, div = 8)
CPU Fan:  3515 RPM  (min =    0 RPM, div = 8)
Aux Fan:     0 RPM  (min =    0 RPM, div = 128)
fan4:        0 RPM  (min = 42187 RPM, div = 32) ALARM
fan5:        0 RPM  (min =    0 RPM, div = 128)
Sys Temp:    +26°C  (high =  +127°C, hyst =  +127°C)
CPU Temp:  +33.0°C  (high = +127.0°C, hyst = +127.0°C)
AUX Temp:  -47.0°C  (high = +127.0°C, hyst = +127.0°C)

Ambient air temp is 75F

---

