---
title: "Hibernate does not restore session"
date: 2019-03-17
forum: Apple Hardware Users
---

### Post by tbrodbeck on 2019-03-17
Hey :). [COLOR=#242729][FONT=Arial]I use a MacBook Pro Late 12, Ubuntu 18.04, i3wm and I have configured 12 Gb of swap (thats 1.5x my RAM size). 

Unfortunately when my laptop tries to hibernate (like with sudo pm-hibernate) it just turns off completely and when I boot again it does not restore the session. I tried out several things, I even installed Manjaro in dual boot, but its just the same in manjaro. I could post a lot of my outputs, but I don't know which is important. I can easily add more stuff if requested.

[/FONT][/COLOR]```
~$ inxi -Fxz
System:    Host: t-MacBookPro Kernel: 4.18.0-16-generic x86_64 bits: 64 gcc: 7.3.0 Desktop: i3 4.14.1
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: Apple product: MacBookPro10 2 v: 1.0 serial: N/A
           Mobo: Apple model: Mac-AFD8A9D944EA4843 v: MacBookPro10 2 serial: N/A
           UEFI: Apple v: 274.0.0.0.0 date: 09/17/2018
Battery    BAT0: charge: 66.6 Wh 97.7% condition: 68.1/73.9 Wh (92%) model: SMP bq20z451 status: Full
           hidpp__0: charge: N/A condition: NA/NA Wh model: Logitech Performance MX status: Discharging
CPU:       Dual core Intel Core i5-3210M (-MT-MCP-) arch: Ivy Bridge rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9976
           clock speeds: max: 3100 MHz 1: 1197 MHz 2: 1197 MHz 3: 1197 MHz 4: 1197 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: intel Resolution: 1680x1050@60.00hz, 1680x1050@59.95hz
           OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile version: 4.2 Mesa 18.2.2 Direct Render: Yes
Audio:     Card Intel 7 Series/C216 Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.18.0-16-generic
Network:   Card-1: Broadcom and subsidiaries NetXtreme BCM57786 Gigabit Ethernet PCIe bus-ID: 02:00.0
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
           Card-2: Broadcom and subsidiaries BCM4331 802.11a/b/g/n driver: bcma-pci-bridge bus-ID: 03:00.0
           IF: wlp3s0b1 state: up mac: <filter>
Drives:    HDD Total Size: 121.3GB (40.4% used)
           ID-1: /dev/sda model: APPLE_SSD_SM128E size: 121.3GB temp: 23C
Partition: ID-1: / size: 45G used: 35G (84%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 12.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 252 Uptime: 15:40 Memory: 2702.0/7851.5MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (fish) inxi: 2.3.56 

```

[COLOR=#242729][FONT=Arial]I am a bit desperate because this is such an important function (otherwise I have to worry about my battery dying all the time) - so anyone trying to help is appreciated. [/FONT][/COLOR]):P

---

### Post by jeremy31 on 2019-03-17
Moved to Apple Hardware

---

