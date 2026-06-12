---
title: "Clean install Ubuntu and New Hard Drive -only problems  Help!"
date: 2019-04-25
forum: Apple Hardware Users
---

### Post by matt8322 on 2019-04-25
I've had an old Macbook Pro laying around for years.  A relative gave it to me and asked me to fix it.  She neglected to give a me a power supply and after repeated requests we both forgot about it.  Was rummaging in my computer storage closet and decided to buy a supply and see what the story was.  Got the "?" screen at boot. Tried a few things and decided the HD was dead.  Rummaged around and found a drive, opened up the computer and NO Hard Drive!  THE HD I had had Win XP istalled so I wiped it and tried to install 19.04 -- Its been days and I have not made much progress.  The computer is a Macbook PRO from mid 2007. Silver lit keyboard, very attractive.

I'm using a USB  with UNbootlin ubuntu 19.04 64 bit on it.  I can boot the live version if I use the safe graphics mode only.  I have installed and reinstalled a number of times, always shows "Ubuntu" then goes to a black screen flashing cursor.  I've read all kinds of directions, have tried resetting Grub partition info, created a EFI partition and no luck.

Can someone point me to step by step directions on how to install when you do not have a hd with OS on it?  I have ZERO experiance wiht Apple products, just want to use this as a laptop in my bedroom for occasional use.  Honestly it should not be this hard.

---

### Post by kc1di on 2019-04-25
Hello matt8322  And welcome to Ubuntu forums,

Most of those came with Nvidia graphics cards and you need to do some work to get them going on Linux.  First you need to append```
 nomodeset
``` to the grub boot line [heres how]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") you do that.  

Good luck.

---

### Post by matt8322 on 2019-04-26
Thanks!  got it up and sort of running now.  Did updates but last time I installed the nvidea driver it no longer would boot.  Edited the grub file so I might try it again.

---

### Post by kc1di on 2019-04-27
Post the output of ```
inxi -Fxz
``` so we know what your actually working with.

---

### Post by matt8322 on 2019-04-27
Ok. Have one other issue to add - won't display after wake from suspend.  I can hear the fans start up as well as the h, but black screen.  Note, I had been trying to install Ubuntu 19, but no luck, switched to Mint 19 and had success, so base is Bionic now

matt@matt-MacBookPro:~$ inxi -Fxz
System:
  Host: matt-MacBookPro Kernel: 4.15.0-48-generic x86_64 bits: 64 
  compiler: gcc v: 7.3.0 Desktop: Cinnamon 4.0.10 
  Distro: Linux Mint 19.1 Tessa base: Ubuntu 18.04 bionic 
Machine:
  Type: Unknown System: Apple product: MacBookPro3,1 v: 1.0 serial: <filter> 
  Mobo: Apple model: Mac-F4238BC8 v: PVT serial: <filter> UEFI: Apple 
  v: MBP31.88Z.0070.B07.0803051658 date: 03/05/08 
CPU:
  Topology: Dual Core model: Intel Core2 Duo T7500 bits: 64 type: MCP 
  arch: Core Merom rev: A L2 cache: 4096 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 vmx bogomips: 8777 
  Speed: 1169 MHz min/max: 800/2200 MHz Core speeds (MHz): 1: 798 2: 798 
Graphics:
  Device-1: NVIDIA G84M [GeForce 8600M GT] vendor: Apple driver: N/A 
  bus ID: 01:00.0 
  Display: x11 server: X.Org 1.19.6 driver: fbdev,nouveau 
  unloaded: modesetting,vesa resolution: 1440x900~77Hz 
  OpenGL: renderer: llvmpipe (LLVM 7.0 128 bits) v: 3.3 Mesa 18.2.8 
  direct render: Yes 
Audio:
  Device-1: Intel 82801H HD Audio vendor: Apple driver: snd_hda_intel 
  v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k4.15.0-48-generic 
Network:
  Device-1: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 
  802.11bgn] 
  vendor: Apple AirPort Extreme driver: ath9k v: kernel port: 5000 
  bus ID: 0b:00.0 
  IF: wls4 state: up mac: <filter> 
  Device-2: Marvell 88E8058 PCI-E Gigabit Ethernet driver: sky2 v: 1.30 
  port: 3000 bus ID: 0c:00.0 
  IF: ens5 state: down mac: <filter> 
Drives:
  Local Storage: total: 74.53 GiB used: 15.92 GiB (21.4%) 
  ID-1: /dev/sda vendor: Fujitsu model: MHV2080BH size: 74.53 GiB 
Partition:
  ID-1: / size: 72.37 GiB used: 15.91 GiB (22.0%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 43.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 181 Uptime: 2m Memory: 1.94 GiB used: 636.9 MiB (32.0%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.3.0 Shell: bash v: 4.4.19 
  inxi: 3.0.27 
matt@matt-MacBookPro:~$

---

