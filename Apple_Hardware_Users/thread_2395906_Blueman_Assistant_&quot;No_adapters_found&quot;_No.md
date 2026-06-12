---
title: "Blueman Assistant &quot;No adapters found&quot; No Bluetooth (2017 Macbook Pro; Ubuntu 18.04)"
date: 2018-07-08
forum: Apple Hardware Users
---

### Post by sdmcduffie on 2018-07-08
Here are my computer's hw and sw specs:


```
mac@macs-MacBookPro:~$ inxi -Fxzd
System:    Host: macs-MacBookPro Kernel: 4.15.0-23-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Cinnamon 3.6.7 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: Apple product: MacBookPro14 1 v: 1.0 serial: N/A
           Mobo: Apple model: Mac-B4831CEBD52A0C4C v: MacBookPro14 1 serial: N/A
           UEFI: Apple v: MBP141.88Z.0173.B00.1802081002 date: 02/08/2018
Battery    BAT0: charge: 21.1 Wh 39.9% condition: 52.9/54.6 Wh (97%)
           model: SMP bq20z451 status: Charging
CPU:       Dual core Intel Core i7-7660U (-MT-MCP-) 
           arch: Kaby Lake rev.9 cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9984
           clock speeds: max: 4000 MHz 1: 3303 MHz 2: 3445 MHz 3: 3195 MHz
           4: 3289 MHz
Graphics:  Card: Intel Device 5926 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 2560x1600@60.00hz
           OpenGL: renderer: Mesa DRI Intel Iris Plus Graphics 640 (Kaby Lake GT3e)
           version: 4.5 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-23-generic
[B]Network:   Card: Broadcom Limited BCM4350 802.11ac Wireless Network Adapter
           driver: brcmfmac bus-ID: 02:00.0[/B]
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.3GB (7.4% used)
           ID-1: /dev/nvme0n1 model: APPLE_SSD_AP0512J size: 500.3GB
           ID-2: /dev/nvme0n2 model: APPLE_SSD_AP0512J size: 0.0GB
           Optical: No optical drives detected.
Partition: ID-1: / size: 317G used: 32G (11%) fs: ext4 dev: /dev/nvme0n1p4
           ID-2: swap-1 size: 4.00GB used: 0.00GB (0%)
           fs: swap dev: /dev/nvme0n1p3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.2C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 272 Uptime: 32 min Memory: 2740.5/15906.7MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```


As you can see, this is a fresh installation of the latest edition of Ubuntu on a one year old Macbook Pro 14,1. I immediately downloaded Blueman as I've had good luck with that in the past on PCs running Linux Mint. When I use Blueman to turn on Bluetooth and then select "set up new device" I get a popup dialog box that tells me there are no adapters.


It's not an issue with my adapter because this is a dual-boot machine and I can switch over to macOS right now and I use my Bluetooth devices so I'm thinking it must be a driver issue.


Anyone have any experience with this or ideas on how I should proceed?

---

### Post by jeremy31 on 2018-07-08
Likely a firmware issue post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by sdmcduffie on 2018-07-08
> **jeremy31 said:**
> Likely a firmware issue post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```


Thanks for the rapid reply. Here are the results...

```
mac@macs-MacBookPro:~$ lsusb; dmesg | egrep -i 'blue|firm'Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.033251] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.053788] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.714247] thunderbolt 0000:06:00.0: starting ICM firmware
[    1.775865] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    4.248253] Bluetooth: Core ver 2.22
[    4.248267] Bluetooth: HCI device and connection manager initialized
[    4.248271] Bluetooth: HCI socket layer initialized
[    4.248274] Bluetooth: L2CAP socket layer initialized
[    4.248279] Bluetooth: SCO socket layer initialized
[    4.253257] Bluetooth: HCI UART driver ver 2.3
[    4.253258] Bluetooth: HCI UART protocol H4 registered
[    4.253259] Bluetooth: HCI UART protocol BCSP registered
[    4.253268] Bluetooth: HCI UART protocol LL registered
[    4.253268] Bluetooth: HCI UART protocol ATH3K registered
[    4.253269] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    4.253283] Bluetooth: HCI UART protocol Intel registered
[    4.253296] Bluetooth: HCI UART protocol Broadcom registered
[    4.253296] Bluetooth: HCI UART protocol QCA registered
[    4.253296] Bluetooth: HCI UART protocol AG6XX registered
[    4.253297] Bluetooth: HCI UART protocol Marvell registered
[    4.414732] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac4350c2-pcie.txt failed with error -2
[    4.689826] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac4350c2-pcie.clm_blob failed with error -2
[    4.690360] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: Nov 26 2015 03:48:57 version 7.35.180.133 (r602372) FWID 01-c45b39d6
[    5.065308] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.065309] Bluetooth: BNEP filters: protocol multicast
[    5.065311] Bluetooth: BNEP socket layer initialized
[    6.304147] Bluetooth: hci0: command 0x0c03 tx timeout
[   14.304223] Bluetooth: hci0: BCM: Reset failed (-110)

```

I also have a sound issue that I mentioned in [another post]("https://ubuntuforums.org/showthread.php?t=2395883"), but Ubuntu works so well on this Macbook Pro that I'd be willing to overlook the lack of internal speakers and the headphone jack if I could just get my Bluetooth speaker to connect.

---

### Post by jeremy31 on 2018-07-08
I am not sure what is wrong with it.  Broadcom bluetooth devices usually show up as USB devices when they are on a PCI wifi card

---

### Post by aejazbasha on 2018-11-10
> **sdmcduffie said:**
> Here are my computer's hw and sw specs:


```
mac@macs-MacBookPro:~$ inxi -Fxzd
System:    Host: macs-MacBookPro Kernel: 4.15.0-23-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Cinnamon 3.6.7 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: Apple product: MacBookPro14 1 v: 1.0 serial: N/A
           Mobo: Apple model: Mac-B4831CEBD52A0C4C v: MacBookPro14 1 serial: N/A
           UEFI: Apple v: MBP141.88Z.0173.B00.1802081002 date: 02/08/2018
Battery    BAT0: charge: 21.1 Wh 39.9% condition: 52.9/54.6 Wh (97%)
           model: SMP bq20z451 status: Charging
CPU:       Dual core Intel Core i7-7660U (-MT-MCP-) 
           arch: Kaby Lake rev.9 cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9984
           clock speeds: max: 4000 MHz 1: 3303 MHz 2: 3445 MHz 3: 3195 MHz
           4: 3289 MHz
Graphics:  Card: Intel Device 5926 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 2560x1600@60.00hz
           OpenGL: renderer: Mesa DRI Intel Iris Plus Graphics 640 (Kaby Lake GT3e)
           version: 4.5 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-23-generic
[B]Network:   Card: Broadcom Limited BCM4350 802.11ac Wireless Network Adapter
           driver: brcmfmac bus-ID: 02:00.0[/B]
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.3GB (7.4% used)
           ID-1: /dev/nvme0n1 model: APPLE_SSD_AP0512J size: 500.3GB
           ID-2: /dev/nvme0n2 model: APPLE_SSD_AP0512J size: 0.0GB
           Optical: No optical drives detected.
Partition: ID-1: / size: 317G used: 32G (11%) fs: ext4 dev: /dev/nvme0n1p4
           ID-2: swap-1 size: 4.00GB used: 0.00GB (0%)
           fs: swap dev: /dev/nvme0n1p3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.2C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 272 Uptime: 32 min Memory: 2740.5/15906.7MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```


As you can see, this is a fresh installation of the latest edition of Ubuntu on a one year old Macbook Pro 14,1. I immediately downloaded Blueman as I've had good luck with that in the past on PCs running Linux Mint. When I use Blueman to turn on Bluetooth and then select "set up new device" I get a popup dialog box that tells me there are no adapters.


It's not an issue with my adapter because this is a dual-boot machine and I can switch over to macOS right now and I use my Bluetooth devices so I'm thinking it must be a driver issue.


Anyone have any experience with this or ideas on how I should proceed?

i am also facing same problem .. how to solve it
blueman error No adapters found
here my system info 
aejaz@aejaz-HP-Laptop-15-bs1xx:~$ inxi -Fxzd

System:    Host: aejaz-HP-Laptop-15-bs1xx Kernel: 4.15.0-36-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3) Distro: Ubuntu 16.04 xenial
Machine:   System: HP product: HP Laptop 15-bs1xx v: Type1ProductConfigId
           Mobo: HP model: 832A v: 23.61 Bios: Insyde v: F.42 date: 08/06/2018
CPU:       Quad core Intel Core i5-8250U (-HT-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 14400
           clock speeds: max: 3400 MHz 1: 817 MHz 2: 1383 MHz 3: 1591 MHz 4: 1797 MHz 5: 1829 MHz 6: 1725 MHz
           7: 1772 MHz 8: 1592 MHz
Graphics:  Card: Intel Device 5917 bus-ID: 00:02.0
           Display Server: X.Org 1.19.3 drivers: (unloaded: fbdev,vesa) Resolution: 1920x1080@60.01hz
           GLX Renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           GLX Version: 3.0 Mesa 18.0.5 Direct Rendering: Yes
Audio:     Card Intel Device 9d71 driver: snd_hda_intel bus-ID: 00:1f.3 Sound: ALSA v: k4.15.0-36-generic
Network:   [COLOR=#ff0000]Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 4000 bus-ID: 01:00.0
           IF: eno1 state: down mac: <filter>
           Card-2: Realtek Device d723 driver: rtl8723de v: v5.1.1.8_21285.20171026 port: 3000 bus-ID: 02:00.0
           IF: wlo1 state: up speed: N/A duplex: N/A mac: <filter>[/COLOR]
Drives:    HDD Total Size: 1000.2GB (4.4% used) ID-1: /dev/sda model: ST1000LM035 size: 1000.2GB temp: 41C
           Optical: /dev/sr0 model: hp DVDRW  DA8AESH rev: XH6M dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 24x multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r state: running
Partition: ID-1: / size: 235G used: 34G (16%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 8.50GB used: 0.00GB (0%) fs: swap dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.5C mobo: 29.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 243 Uptime: 1:12 Memory: 1397.6/7893.5MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

---

### Post by aejazbasha on 2018-11-10
> **jeremy31 said:**
> Likely a firmware issue post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```


after executing that command i got this.

aejaz@aejaz-HP-Laptop-15-bs1xx:~$ lsusb; dmesg | egrep -i 'blue|firm'

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c9b Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   24.983563] RTW: rtl8723d_FirmwareDownload((null)) tmp_ps=0
[   24.983565] RTW: rtl8723d_FirmwareDownload fw: FW_NIC, size: 26498
[   24.983566] RTW: rtl8723d_FirmwareDownload: fw_ver=1d fw_subver=0002 sig=0x23d1, Month=04, Date=14, Hour=11, Minute=13
[   24.983566] RTW: rtl8723d_FirmwareDownload(): Shift for fw header!
[   24.983568] RTW: rtl8723d_FirmwareDownload by IO write!
[   24.986044] RTW: rtl8723d_FirmwareDownload: download FW count:1
[   25.004247] RTW: rtl8723d_FirmwareDownload success. write_fw:1, 24ms
[   25.004248] RTW:  <=== rtl8723d_FirmwareDownload()
[   29.490025] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.490027] Bluetooth: BNEP filters: protocol multicast
[   29.490031] Bluetooth: BNEP socket layer initialized
[   33.157484] RTW: rtl8723d_FirmwareDownload(wlo1) tmp_ps=0
[   33.157485] RTW: rtl8723d_FirmwareDownload fw: FW_NIC, size: 26498
[   33.157489] RTW: rtl8723d_FirmwareDownload: fw_ver=1d fw_subver=0002 sig=0x23d1, Month=04, Date=14, Hour=11, Minute=13
[   33.157489] RTW: rtl8723d_FirmwareDownload(): Shift for fw header!
[   33.157560] RTW: rtl8723d_FirmwareDownload by IO write!
[   33.159957] RTW: rtl8723d_FirmwareDownload: download FW count:1
[   33.178160] RTW: rtl8723d_FirmwareDownload success. write_fw:1, 20ms
[   33.178161] RTW:  <=== rtl8723d_FirmwareDownload()
[   35.091787] RTW: rtl8723d_FirmwareDownload(wlo1) tmp_ps=0
[   35.091787] RTW: rtl8723d_FirmwareDownload fw: FW_NIC, size: 26498
[   35.091789] RTW: rtl8723d_FirmwareDownload: fw_ver=1d fw_subver=0002 sig=0x23d1, Month=04, Date=14, Hour=11, Minute=13
[   35.091789] RTW: rtl8723d_FirmwareDownload(): Shift for fw header!
[   35.091873] RTW: rtl8723d_FirmwareDownload by IO write!
[   35.094271] RTW: rtl8723d_FirmwareDownload: download FW count:1
[   35.112474] RTW: rtl8723d_FirmwareDownload success. write_fw:1, 24ms
[   35.112475] RTW:  <=== rtl8723d_FirmwareDownload()
[   58.021783] RTW: rtl8723d_FirmwareDownload(wlo1) tmp_ps=0
[   58.021784] RTW: rtl8723d_FirmwareDownload fw: FW_NIC, size: 26498
[   58.021785] RTW: rtl8723d_FirmwareDownload: fw_ver=1d fw_subver=0002 sig=0x23d1, Month=04, Date=14, Hour=11, Minute=13
[   58.021786] RTW: rtl8723d_FirmwareDownload(): Shift for fw header!
[   58.021869] RTW: rtl8723d_FirmwareDownload by IO write!
[   58.024341] RTW: rtl8723d_FirmwareDownload: download FW count:1
[   58.042544] RTW: rtl8723d_FirmwareDownload success. write_fw:1, 20ms
[   58.042544] RTW:  <=== rtl8723d_FirmwareDownload()
[   79.518970] RTW: rtl8723d_FirmwareDownload(wlo1) tmp_ps=0
[   79.518971] RTW: rtl8723d_FirmwareDownload fw: FW_NIC, size: 26498
[   79.518972] RTW: rtl8723d_FirmwareDownload: fw_ver=1d fw_subver=0002 sig=0x23d1, Month=04, Date=14, Hour=11, Minute=13
[   79.518973] RTW: rtl8723d_FirmwareDownload(): Shift for fw header!
[   79.519056] RTW: rtl8723d_FirmwareDownload by IO write!
[   79.521539] RTW: rtl8723d_FirmwareDownload: download FW count:1
[   79.539817] RTW: rtl8723d_FirmwareDownload success. write_fw:1, 20ms
[   79.539818] RTW:  <=== rtl8723d_FirmwareDownload()

---

