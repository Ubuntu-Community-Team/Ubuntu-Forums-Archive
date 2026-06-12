---
title: "G73S System Completely Freezes Under 11.04 and 10.04"
date: 2011-09-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dano2 on 2011-09-06
Today, I finally got ubuntu 10.04 installed after 11.04 kept freezing up on me. Now 10.04 is freezing up the same way. The entire system except the mouse. I control-alt-delete and can only watch helplessly as it counts down to shut down. 

Are there some known Asus/Ubuntu compatibility issues? This laptop is brand new, and I need Ubuntu for web development. So this is really a bummer.


ASUS
Model
G73SW-XN2
CPU Type
Intel Core i7-2630QM 2.0GHz
Screen
17.3" FHD
Memory Size
8GB DDR3
Hard Disk
500GB
Optical Drive
DVD Super Multi
Graphics Card
NVIDIA GeForce GTX 460M
Video Memory
1.5GB GDDR5 VRAM
Communication
Gigabit LAN and WLAN
Dimensions
16.60" x 12.80" x 0.80" - 2.30"
Weight
8.00 lbs.
CPU
CPU Type
Intel Core i7
CPU Speed
2630QM(2.00GHz)
CPU Support
Quad Core Processor
6MB L3 Cache
Turbo Boost up to 2.9GHz
Chipset
Chipset
Intel HM65
Resolution
1920 x 1080
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834230028](http://www.newegg.com/Product/Product.aspx?Item=N82E16834230028)

---

### Post by dano2 on 2011-09-06
Any thoughts?

---

### Post by dummy910 on 2011-09-06
Don't be bummed, **this laptop screams with Ubuntu installed on it**, as I too have an AsusG73, same specs except mine has the ATI5850 video card and only 6gb of RAM installed, and everything except the hibernation feature of Ubuntu works(I never use this feature on any machine, so I always disable from the get go), and from the 1st boot after the install finished.  

_Have you looked at your logs_(?) as there should be some lines that show **error** or **fail**....

My G73 Ubuntu experience has been 110% as this laptop leaves Win7 way back into a plum of dust on every level of performance, beginning with the boot times onward....

---

### Post by dano2 on 2011-09-07
> **dummy910 said:**
> Don't be bummed, **this laptop screams with Ubuntu installed on it**, as I too have an AsusG73, same specs except mine has the ATI5850 video card and only 6gb of RAM installed, and everything except the hibernation feature of Ubuntu works(I never use this feature on any machine, so I always disable from the get go), and from the 1st boot after the install finished.  

_Have you looked at your logs_(?) as there should be some lines that show **error** or **fail**....

My G73 Ubuntu experience has been 110% as this laptop leaves Win7 way back into a plum of dust on every level of performance, beginning with the boot times onward....


Well that's good news. Is there a particular log a system freeze would be more likely to show up in? I grepped /var/log/syslog.1 for "fail" and "error", but I'm not really sure what I should be looking for. I think it occurred around "Sep  6 02:25" but not sure. I'll make note of the exact time when it happens again.

[PHP]

dfs@sdf:~$ cat /var/log/syslog.1 | grep fail
Sep  6 02:25:44 udlap kernel: [    0.941542] Not enabling x2apic, Intr-remapping init failed.
Sep  6 02:25:44 udlap kernel: [    2.180759] PM: Resume from disk failed.
Sep  6 02:25:53 udlap gdm-session-worker[1385]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep  6 02:26:00 udlap NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  6 02:26:00 udlap NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  6 14:21:32 udlap kernel: [    0.929784] Not enabling x2apic, Intr-remapping init failed.
Sep  6 14:21:32 udlap kernel: [    2.168010] PM: Resume from disk failed.
Sep  6 14:21:42 udlap gdm-session-worker[1372]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep  6 14:21:47 udlap NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  6 14:21:47 udlap NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  7 00:58:36 udlap kernel: [38219.288143] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Sep  7 06:26:49 udlap kernel: [57904.309254] ath9k: RX failed to go idle in 10 ms RXSM=0xdeadbeef
Sep  7 06:27:15 udlap kernel: [57930.341750] ath9k: RX failed to go idle in 10 ms RXSM=0xdeadbeef
Sep  7 06:27:30 udlap kernel: [57945.525017] ath9k: RX failed to go idle in 10 ms RXSM=0xdeadbeef
Sep  7 06:27:44 udlap kernel: [57958.886660] ath9k: RX failed to go idle in 10 ms RXSM=0xdeadbeef
Sep  7 06:27:57 udlap kernel: [57972.205860] ath9k: RX failed to go idle in 10 ms RXSM=0xdeadbeef


dfs@sdf:~$ cat /var/log/syslog.1 | grep error
Sep  6 02:25:45 udlap NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep  6 14:21:32 udlap init: Failed to open system console: Input/output error
Sep  6 14:21:32 udlap NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files


[/PHP]


Thanks!

---

