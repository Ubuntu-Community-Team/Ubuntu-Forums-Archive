---
title: "Intel Ethernet I217-V"
date: 2020-12-24
forum: Any Other OS
---

### Post by i217v on 2020-12-24
Hiya
When I try and run any linux distribution other then ubuntu i am unable to connect to the internet

mint@mint:~$ inxi -Fxxxz
```

System:    Kernel: 5.4.0-26-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Cinnamon 4.6.6 wm: muffin 4.6.2 
           dm: LightDM 1.30.0 Distro: Linux Mint 20 Ulyana base: Ubuntu 20.04 focal 
Machine:   Type: Desktop System: ASUS product: All Series v: N/A serial: <filter> 
           Mobo: ASUSTeK model: MAXIMUS VI HERO v: Rev 1.xx serial: <filter> UEFI: American Megatrends v: 1603 
           date: 08/15/2014 
Battery:   Device-1: hidpp_battery_0 model: Logitech K350 serial: <filter> charge: 70% (should be ignored) rechargeable: yes 
           status: Discharging 
CPU:       Topology: Quad Core model: Intel Core i7-4770K bits: 64 type: MT MCP arch: Haswell rev: 3 L2 cache: 8192 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 56000 
           Speed: 900 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 1064 2: 1667 3: 1265 4: 1968 5: 2347 6: 2471 7: 2395 
           8: 2426 
Graphics:  Device-1: NVIDIA GP102 [GeForce GTX 1080 Ti] vendor: ASUSTeK driver: nouveau v: kernel bus ID: 01:00.0 
           chip ID: 10de:1b06 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: NV132 v: 4.3 Mesa 20.0.4 direct render: Yes 
Audio:     Device-1: NVIDIA GP102 HDMI Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           chip ID: 10de:10ef 
           Device-2: Creative Labs EMU20k2 [Sound Blaster X-Fi Titanium Series] driver: snd_ctxfi v: kernel bus ID: 03:00.0 
           chip ID: 1102:000b 
           Sound Server: ALSA v: k5.4.0-26-generic 
Network:   Device-1: Intel Ethernet I217-V vendor: ASUSTeK driver: e1000e v: 3.2.6-k port: f040 bus ID: 00:19.0 
           chip ID: 8086:153b 
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 908.66 GiB used: 31.68 GiB (3.5%) 
           ID-1: /dev/sda vendor: Crucial model: CT960M500SSD1 size: 894.25 GiB speed: 6.0 Gb/s serial: <filter> rev: MU05 
           temp: 35 C scheme: GPT 
           ID-2: /dev/sdb type: USB vendor: Kingston model: DataTraveler 3.0 size: 14.41 GiB serial: <filter> scheme: GPT 
Partition: ID-1: / size: 11.71 GiB used: 53.7 MiB (0.4%) fs: overlay source: ERR-102 
Sensors:   System Temperatures: cpu: 50.0 C mobo: 27.8 C gpu: nouveau temp: 39 C 
           Fan Speeds (RPM): N/A gpu: nouveau fan: 1388 
Info:      Processes: 256 Uptime: 2m Memory: 23.43 GiB used: 1.01 GiB (4.3%) Init: systemd v: 245 runlevel: 5 Compilers: 
           gcc: 9.3.0 alt: 9 Shell: bash v: 5.0.16 running in: gnome-terminal inxi: 3.0.38 
 
```
mint@mint:~$ mokutil --sb-state
```

SecureBoot disabled

```
mint@mint:~$ rfkill list
mint@mint:~$ iwconfig
```

eno1      no wireless extensions.


lo        no wireless extensions.

```
mint@mint:~$ lsusb
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c08b Logitech, Inc. G502 HERO Gaming Mouse
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
mint@mint:~$  lspci 
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP102 HDMI Audio Controller (rev a1)
03:00.0 Audio device: Creative Labs EMU20k2 [Sound Blaster X-Fi Titanium Series] (rev 03)

```


using this motherboard
[https://www.asus.com/us/Motherboards/MAXIMUS_VI_HERO/](https://www.asus.com/us/Motherboards/MAXIMUS_VI_HERO/)
this network adapter
[https://ark.intel.com/content/www/us/en/ark/products/70831/intel-ethernet-connection-i217-v.html](https://ark.intel.com/content/www/us/en/ark/products/70831/intel-ethernet-connection-i217-v.html)
[https://www.intel.com/content/www/us/en/products/network-io/ethernet/controllers/connection-i217-v.html](https://www.intel.com/content/www/us/en/products/network-io/ethernet/controllers/connection-i217-v.html)

both Ubuntu 20.04.1 LTS & Ubuntu 20.10 work with a minor bug at boot if you press any button while ubuntu loads it breaks network connectivity and must reboot whole pc to fix happens while trying to push Ctrl+C to skip verify if you push wrong key

other linux os's i have tried that will not work thus far are
[https://linuxmint.com/](https://linuxmint.com/)
[https://tails.boum.org/](https://tails.boum.org/)
[https://getfedora.org/](https://getfedora.org/)
[https://www.centos.org/](https://www.centos.org/)
[https://www.redhat.com/en](https://www.redhat.com/en)
[https://parrotlinux.org/](https://parrotlinux.org/)

versions of windows that work
[https://en.wikipedia.org/wiki/Windows_X ... 64_Edition]("https://en.wikipedia.org/wiki/Windows_XP_Professional_x64_Edition")
[https://en.wikipedia.org/wiki/Windows_7](https://en.wikipedia.org/wiki/Windows_7)
[https://en.wikipedia.org/wiki/Windows_10](https://en.wikipedia.org/wiki/Windows_10)
[https://en.wikipedia.org/wiki/Windows_IoT#Enterprise](https://en.wikipedia.org/wiki/Windows_IoT#Enterprise)
[https://en.wikipedia.org/wiki/Windows_Server](https://en.wikipedia.org/wiki/Windows_Server)

I am trying to run the linux os's live and have not installed yet but thus far nothing linux seems compatible with my computer hardware

---

