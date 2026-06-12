---
title: "2017 Macbook Pro 14,1 running Ubuntu 18.04 LTS: No sound (internal or audio jack)"
date: 2018-07-08
forum: Apple Hardware Users
---

### Post by sdmcduffie on 2018-07-08
Here is my machine's hardware and software information:


```
mac@macs-MacBookPro:~$ inxi -Fxzd
System:    Host: macs-MacBookPro Kernel: 4.15.0-23-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Cinnamon 3.6.7 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: Apple product: MacBookPro14 1 v: 1.0 serial: N/A
           Mobo: Apple model: Mac-B4831CEBD52A0C4C v: MacBookPro14 1 serial: N/A
           UEFI: Apple v: MBP141.88Z.0173.B00.1802081002 date: 02/08/2018
Battery    BAT0: charge: 51.4 Wh 98.2% condition: 52.3/54.6 Wh (96%)
           model: SMP bq20z451 status: Full
CPU:       Dual core Intel Core i7-7660U (-MT-MCP-) 
           arch: Kaby Lake rev.9 cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9984
           clock speeds: max: 4000 MHz 1: 600 MHz 2: 600 MHz 3: 600 MHz
           4: 600 MHz
Graphics:  Card: Intel Device 5926 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 2560x1600@60.00hz
           OpenGL: renderer: Mesa DRI Intel Iris Plus Graphics 640 (Kaby Lake GT3e)
           version: 4.5 Mesa 18.0.0-rc5 Direct Render: Yes
A[B]udio:     Card Intel Sunrise Point-LP HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-23-generic[/B]
Network:   Card: Broadcom Limited BCM4350 802.11ac Wireless Network Adapter
           driver: brcmfmac bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 8501.8GB (83.1% used)
           ID-1: /dev/nvme0n1 model: APPLE_SSD_AP0512J size: 500.3GB
           ID-2: /dev/nvme0n2 model: APPLE_SSD_AP0512J size: 0.0GB
           ID-3: USB /dev/sdc model: My_Book_25EE size: 8001.6GB
           Optical: No optical drives detected.
Partition: ID-1: / size: 317G used: 31G (11%) fs: ext4 dev: /dev/nvme0n1p4
           ID-2: swap-1 size: 4.00GB used: 0.00GB (0%)
           fs: swap dev: /dev/nvme0n1p3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 67.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 285 Uptime: 3:24 Memory: 3002.5/15906.7MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```


I have no audio at all. I sort of expected not to have use of the internal speakers (without some tweaking) but I expected to have sound output through the headphone jack.


Any ideas on where I should go from here? I've googled a bit and haven't found a good answer.

---

### Post by wildmanne39 on 2018-07-08
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by ubonetu2 on 2018-07-25
I'm having less of a problem but my audio input with either a dual to single adaptor or a cell phone mic is distorted and very quiet.  I have output and have tried everything I could find on the web.

I tried several drivers in 

```
sudo vim /etc/modprobe.d/alsa-base.conf 
```

# [https://askubuntu.com/questions/984239/no-microphone-picked-up-on-ubuntu-16-04-on-macbook-pro](https://askubuntu.com/questions/984239/no-microphone-picked-up-on-ubuntu-16-04-on-macbook-pro)
#options snd-hda-intel model=mbp101
#options snd-hda-intel model=macpro
#options snd-hda-intel model=mbp3
#options snd-hda-intel model=mbp55

Maybe one of the drives would work for you (just reboot when you add one at the end of alsa-base.conf)?

Here's my system info:

```
wardbones@ubuntu-MacBookPro:~$ inxi -FxzdSystem:    Host: ubuntu-MacBookPro Kernel: 4.15.0-29-lowlatency x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.2 (Gtk 3.22.30-1ubuntu1) Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Apple product: MacBookPro8 1 v: 1.0 serial: N/A
           Mobo: Apple model: Mac-94245B3640C91C81 v: MacBookPro8 1 serial: N/A
           BIOS: Apple v: MBP81.88Z.0050.B00.1804101331 date: 04/10/18
Battery    BAT0: charge: 50.5 Wh 96.5% condition: 52.3/62.9 Wh (83%) model: SMP bq20z451 status: Full
CPU:       Dual core Intel Core i5-2415M (-MT-MCP-) arch: Sandy Bridge rev.7 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9178
           clock speeds: max: 2900 MHz 1: 1883 MHz 2: 2018 MHz 3: 1473 MHz 4: 2251 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x800@60.22hz
           OpenGL: renderer: Mesa DRI Intel Sandybridge Mobile version: 3.3 Mesa 18.0.5 Direct Render: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-29-lowlatency
Network:   Card-1: Broadcom Limited NetXtreme BCM57765 Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: enp2s0f0 state: down mac: <filter>
           Card-2: Broadcom Limited BCM4331 802.11a/b/g/n driver: wl bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 2000.4GB (55.8% used)
           ID-1: /dev/sda model: MD1TBLSSHD size: 1000.2GB
           ID-2: FireWire /dev/sdb model: 541010A9E680 size: 1000.2GB
           Optical-1: /dev/sr0 model: MATSHITA DVD-R   UJ-898 rev: HC10 dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 24x multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r state: running
Partition: ID-1: / size: 915G used: 384G (45%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 705M used: 146M (23%) fs: ext4 dev: /dev/sda2
           ID-3: swap-1 size: 1.02GB used: 0.00GB (0%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 64.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 314 Uptime: 1:11 Memory: 2510.0/7887.5MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 



```

---

