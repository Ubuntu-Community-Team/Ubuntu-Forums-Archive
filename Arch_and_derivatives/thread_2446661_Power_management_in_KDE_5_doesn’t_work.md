---
title: "Power management in KDE 5 doesn’t work"
date: 2020-07-04
forum: Arch and derivatives
---

### Post by Perfect Storm on 2020-07-04
Hello,

I have noticed that Power Management in Manjaro Plasma doesn't work. Well it work with its default 10 min switch off, but whatever changes you make in there haven't any affect.

Some more info:
```
root=UUID=b284a2e6-9b01-441b-b98c-8c10b0f51211 rw quiet 
  udev.log_priority=3 
  Desktop: KDE Plasma 5.18.5 tk: Qt 5.15.0 info: latte-dock wm: kwin_x11 
  dm: SDDM Distro: Manjaro Linux 
Machine:
  Type: Desktop Mobo: ASUSTeK model: PRIME X370-A v: Rev X.0x 
  serial: <filter> UEFI: American Megatrends v: 0805 date: 06/20/2017 
Battery:
  Device-1: hidpp_battery_0 model: Logitech Wireless Solar Keyboard K750 
  serial: <filter> charge: 95% rechargeable: yes status: Charging 
  Device-2: hidpp_battery_1 
  model: Logitech Marathon Mouse/Performance Plus M705 serial: <filter> 
  charge: 55% (should be ignored) rechargeable: yes status: Discharging 
CPU:
  Topology: 8-Core model: AMD Ryzen 7 1700X bits: 64 type: MT MCP 
  arch: Zen family: 17 (23) model-id: 1 stepping: 1 microcode: 8001126 
  L2 cache: 4096 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 108625 
  Speed: 2033 MHz min/max: 2200/3400 MHz boost: enabled 
  Core speeds (MHz): 1: 1818 2: 1825 3: 1812 4: 1826 5: 1732 6: 1834 
  7: 1715 8: 1804 9: 1745 10: 1729 11: 1730 12: 1734 13: 3324 14: 2525 
  15: 1926 16: 2385 
  Vulnerabilities: Type: itlb_multihit status: Not affected 
  Type: l1tf status: Not affected 
  Type: mds status: Not affected 
  Type: meltdown status: Not affected 
  Type: spec_store_bypass 
  mitigation: Speculative Store Bypass disabled via prctl and seccomp 
  Type: spectre_v1 
  mitigation: usercopy/swapgs barriers and __user pointer sanitization 
  Type: spectre_v2 
  mitigation: Full AMD retpoline, STIBP: disabled, RSB filling 
  Type: tsx_async_abort status: Not affected 
Graphics:
  Device-1: NVIDIA GP104 [GeForce GTX 1070] vendor: ASUSTeK 
  driver: nvidia v: 440.82 bus ID: 2a:00.0 chip ID: 10de:1b81 
  Display: x11 server: X.Org 1.20.8 driver: nvidia compositor: kwin_x11 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GTX 1070/PCIe/SSE2 v: 4.6.0 NVIDIA 440.82 
  direct render: Yes 
Audio:
  Device-1: NVIDIA GP104 High Definition Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 2a:00.1 chip ID: 10de:10f0 
  Device-2: AMD Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel 
  v: kernel bus ID: 2c:00.3 chip ID: 1022:1457 
  Sound Server: ALSA v: k5.6.16-1-MANJARO 
Network:
  Device-1: Qualcomm Atheros AR9227 Wireless Network Adapter 
  driver: ath9k v: kernel bus ID: 27:01.0 chip ID: 168c:002d 
  IF: wlp39s1 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASUSTeK driver: r8169 v: kernel port: f000 bus ID: 28:00.0 
  chip ID: 10ec:8168 
  IF: enp40s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 1.14 TiB used: 12.96 GiB (1.1%) 
  ID-1: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB 
  size: 232.89 GiB block size: physical: 512 B logical: 512 B 
  speed: 6.0 Gb/s serial: <filter> rev: 2B6Q scheme: MBR 
  ID-2: /dev/sdb vendor: Toshiba model: DT01ACA100 size: 931.51 GiB 
  block size: physical: 4096 B logical: 512 B speed: 6.0 Gb/s 
  rotation: 7200 rpm serial: <filter> rev: A750 scheme: GPT 
Partition:
  ID-1: / raw size: 232.42 GiB size: 227.77 GiB (98.00%) 
  used: 9.38 GiB (4.1%) fs: ext4 dev: /dev/sda5 
  ID-2: /home raw size: 931.51 GiB size: 915.89 GiB (98.32%) 
  used: 3.57 GiB (0.4%) fs: ext4 dev: /dev/sdb1 
Sensors:
  System Temperatures: cpu: 48.1 C mobo: N/A gpu: nvidia temp: 52 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 0% 
Info:
  Processes: 325 Uptime: 1h 10m Memory: 31.36 GiB used: 2.74 GiB (8.7%) 
  Init: systemd v: 245 Compilers: gcc: 10.1.0 Shell: bash v: 5.0.17 
  running in: konsole inxi: 3.0.37 
[storm@universe ~]$ 
```

I found out that it's the powerdevil that is not working properly.
Here's the output:
```
Couldn't load plugin "kcms/kcm_powerdevilprofilesconfig" : "The shared library was not found."  -- falling back to old-style loading from desktop file
powerdevil: ("LowBattery", "migration", "Battery", "AC") ()
powerdevil: "Keyboard backlight"  has a runtime requirement
powerdevil: The action  QVariant(QString, "KeyboardBrightnessControl")  appears not to be supported by the core.
powerdevil: "Wireless"  has a runtime requirement
powerdevil: "Screen brightness"  has a runtime requirement
powerdevil: The action  QVariant(QString, "BrightnessControl")  appears not to be supported by the core.
powerdevil: "Screen Energy Saving"  has a runtime requirement
powerdevil: "Button events handling"  has a runtime requirement
powerdevil: "Dim screen"  has a runtime requirement
powerdevil: The action  QVariant(QString, "DimDisplay")  appears not to be supported by the core.
powerdevil: "Keyboard backlight"  has a runtime requirement
powerdevil: The action  QVariant(QString, "KeyboardBrightnessControl")  appears not to be supported by the core.
powerdevil: "Wireless"  has a runtime requirement
powerdevil: "Screen brightness"  has a runtime requirement
powerdevil: The action  QVariant(QString, "BrightnessControl")  appears not to be supported by the core.
powerdevil: "Screen Energy Saving"  has a runtime requirement
powerdevil: "Button events handling"  has a runtime requirement
powerdevil: "Dim screen"  has a runtime requirement
powerdevil: The action  QVariant(QString, "DimDisplay")  appears not to be supported by the core.
powerdevil: "Keyboard backlight"  has a runtime requirement
powerdevil: The action  QVariant(QString, "KeyboardBrightnessControl")  appears not to be supported by the core.
powerdevil: "Wireless"  has a runtime requirement
powerdevil: "Screen brightness"  has a runtime requirement
powerdevil: The action  QVariant(QString, "BrightnessControl")  appears not to be supported by the core.
powerdevil: "Screen Energy Saving"  has a runtime requirement
powerdevil: "Button events handling"  has a runtime requirement
powerdevil: "Dim screen"  has a runtime requirement
powerdevil: The action  QVariant(QString, "DimDisplay")  appears not to be supported by the core.
powerdevil: Loading routine called
powerdevil: ()
powerdevil: Ok, KConfigGroup ready ("icon")
powerdevil: ()
powerdevil: Ok, KConfigGroup ready ("icon")
powerdevil: ()
powerdevil: Ok, KConfigGroup ready ("icon")

```

---

### Post by Perfect Storm on 2020-07-05
Problem solved after installing the driver. :p

---

