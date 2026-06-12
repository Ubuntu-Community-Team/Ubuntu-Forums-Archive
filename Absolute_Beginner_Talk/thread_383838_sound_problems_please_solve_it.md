---
title: "sound problems please solve it"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-13
guys i cant use headphone i already made two thread nobody were able to help me.. they say to go alsa mixer and check headphone but i dont have a headphone listed there.. please help me..

---

### Post by HunkieChan on 2007-03-13
can anybody help me , please ?

---

### Post by mikewhatever on 2007-03-13
What do you need?

---

### Post by HunkieChan on 2007-03-13
> **mikewhatever said:**
> What do you need?

i want to use headphone but the sound comes out throught speaker..

---

### Post by glotz on 2007-03-13
Goto alsamixer edit > prefs and select headphones?

When I plug in my headphones to my mini stereo jacked to my box, the speakers are muted automagically.

---

### Post by HunkieChan on 2007-03-13
> **glotz said:**
> Goto alsamixer edit > prefs and select headphones?

When I plug in my headphones to my mini stereo jacked to my box, the speakers are muted automagically.

there is no headphone in there.. thats the problem

---

### Post by mikewhatever on 2007-03-13
since you don't give up your sound card specs, I'd suggest searching the forums. I've gone over the two previous posts. People there suggested several things and you say it didn't work. [http://ubuntuforums.org/showthread.php?t=383213](http://ubuntuforums.org/showthread.php?t=383213) What exactly? Have you succeeded turning the headphone jack on? Can you post the screen shots of your alsamixer and volume control windows.

---

### Post by HunkieChan on 2007-03-13
> **mikewhatever said:**
> since you don't give up your sound card specs, I'd suggest searching the forums. I've gone over the two previous posts. People there suggested several things and you say it didn't work. [http://ubuntuforums.org/showthread.php?t=383213](http://ubuntuforums.org/showthread.php?t=383213) What exactly? Have you succeeded turning the headphone jack on? Can you post the screen shots of your alsamixer and volume control windows.

[[IMG]http://img410.imageshack.us/img410/9194/screenshotxw4.th.png[/IMG]](http://img410.imageshack.us/my.php?image=screenshotxw4.png)

# AMD Turion 64 X2 Mobile TL-52 (1.60GHz/512KB)
# 14.1" WXGA BrightView Widescreen (1280 x 800)
# NVIDIA GeForce Go 6150
# 512MB DDR2 SDRAM (2x256MB)*
# 60 GB 5400 RPM Serial ATA Hard Drive
# Super Multi 8X DVD+/-R/RW w/Double Layer Support
# 802.11b/g WLAN
# 12 Cell Lithium Ion Battery
# 1-yr Standard Warranty
# Dimensions: 13.15" (L) x 9.33" (W) x 1" (min H)/1.54" (max H)
# Weight (6 cell): 5.5lb


thats all i got..

---

### Post by HunkieChan on 2007-03-13
any one ? please ?

---

### Post by mikewhatever on 2007-03-13
Still no sound card specs. Where is the alsamixer window? Do you really need help, or is this a joke?

Type lshw in the terminal.

---

### Post by HunkieChan on 2007-03-13
> **mikewhatever said:**
> Still no sound card specs. Where is the alsamixer window? Do you really need help, or is this a joke?

Type lshw in the terminal.

[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&series_name=V3000Z_series&tab_switch=true&catLevel=3&tab=specs](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&series_name=V3000Z_series&tab_switch=true&catLevel=3&tab=specs)

this is my computer.. i think its says intergreted altec speaker.. is that the one ?

---

### Post by mikewhatever on 2007-03-14
> **HunkieChan said:**
> [http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&series_name=V3000Z_series&tab_switch=true&catLevel=3&tab=specs](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&series_name=V3000Z_series&tab_switch=true&catLevel=3&tab=specs)

this is my computer.. i think its says intergreted altec speaker.. is that the one ?

Try posting the output of lshw command.

---

### Post by HunkieChan on 2007-03-14
> **mikewhatever said:**
> Try posting the output of lshw command.

description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 447MB
     *-cpu
          product: Mobile AMD Sempron(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni cx16 lahf_lm cr8legacy ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-network DISABLED
             description: Wireless interface
             product: BCM4310 UART
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@01:00.0
             logical name: eth1
             version: 01
             serial: 00:1a:73:00:93:93
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:c3000000-c3003fff irq:233
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          size: 256MB
          width: 64 bits
          clock: 66MHz
          capabilities: vga bus_master cap_list
          configuration: driver=nvidia
          resources: iomemory:c2000000-c2ffffff iomemory:d0000000-dfffffff iomemory:c1000000-c1ffffff irq:217
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-isa UNCLAIMED
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
     *-serial UNCLAIMED
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          resources: ioport:3040-307f ioport:3000-303f irq:10
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          resources: iomemory:c0040000-c007ffff irq:11
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:c0004000-c0004fff irq:217
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.17-11-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=8 speed=12.0MB/s
           *-usb
                description: Mouse
                product: USB Receiver
                vendor: Logitech
                physical id: 6
                bus info: usb@2:6
                version: 34.10
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:c0005000-c00050ff irq:209
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.17-11-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE
          resources: ioport:3080-308f
        *-ide
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom
                product: HL-DT-STCD-RW/DVD DRIVE GCC-4244N
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                capabilities: packet
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          logical name: scsi0
          logical name: scsi1
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv
          resources: ioport:30b0-30b7 ioport:30a4-30a7 ioport:30a8-30af ioport:30a0-30a3 ioport:3090-309f iomemory:c0006000-c0006fff irq:201
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel
          resources: iomemory:c0000000-c0003fff irq:50
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@00:14.0
          logical name: eth0
          version: a3
          serial: 00:16:d3:1a:40:03
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth ip=192.168.1.40 multicast=yes
          resources: iomemory:c0007000-c0007fff ioport:30b8-30bf irq:225
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by mikewhatever on 2007-03-14
So, your audio device is:
*-multimedia
description: Audio device
product: MCP51 High Definition Audio
vendor: nVidia Corporation
physical id: 10.1
bus info: pci@00:10.1
version: a2
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel
resources: iomemory:c0000000-c0003fff irq:50

and the solution to most of its sound/mic problems is here [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

---

### Post by HunkieChan on 2007-03-14
> **mikewhatever said:**
> So, your audio device is:
*-multimedia
description: Audio device
product: MCP51 High Definition Audio
vendor: nVidia Corporation
physical id: 10.1
bus info: pci@00:10.1
version: a2
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel
resources: iomemory:c0000000-c0003fff irq:50

and the solution to most of its sound/mic problems is here [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

thanks a lot

---

### Post by HunkieChan on 2007-03-14
okay that site links me to download alsa driver. and the page doesnt load or its not there anymore.. is there any alternative ?

---

### Post by mikewhatever on 2007-03-14
> **HunkieChan said:**
> okay that site links me to download alsa driver. and the page doesnt load or its not there anymore.. is there any alternative ?

It was temporarily unavailable, but loads now.

---

### Post by HunkieChan on 2007-03-14
> **mikewhatever said:**
> It was temporarily unavailable, but loads now.

    *
      Setup installation directories
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp /home/naaman/installers/alsa/* .
sudo tar xjf alsa-driver-1.0.14rc1.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc1.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc1.tar.bz2
 

they ask me to do this ^ when i put it in... i get this error

hunkiechan@HunkieChanUniverse:~$ sudo mkdir -p /usr/src/alsa
hunkiechan@HunkieChanUniverse:~$ cd /usr/src/alsa
hunkiechan@HunkieChanUniverse:/usr/src/alsa$ sudo cp /home/naaman/installers/alsa/* .
cp: cannot stat `/home/naaman/installers/alsa/*': No such file or directory


what should i do ?

---

### Post by mikewhatever on 2007-03-14
> **HunkieChan said:**
> *
      Setup installation directories
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp /home/naaman/installers/alsa/* .
sudo tar xjf alsa-driver-1.0.14rc1.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc1.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc1.tar.bz2
 

they ask me to do this ^ when i put it in... i get this error

hunkiechan@HunkieChanUniverse:~$ sudo mkdir -p /usr/src/alsa
hunkiechan@HunkieChanUniverse:~$ cd /usr/src/alsa
hunkiechan@HunkieChanUniverse:/usr/src/alsa$ sudo cp /home/naaman/installers/alsa/* .
cp: cannot stat `/home/naaman/installers/alsa/*': No such file or directory


what should i do ?

Skip the cp part and continue from /usr/src/alsa directory. Go to /usr/src/alsa directory again using 'cd' command and then run
sudo tar xjf alsa-driver-1.0.14rc1.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc1.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc1.tar.bz2

and all the rest.

---

### Post by HunkieChan on 2007-03-14
> **mikewhatever said:**
> Skip the cp part and continue from /usr/src/alsa directory. Go to /usr/src/alsa directory again using 'cd' command and then run
sudo tar xjf alsa-driver-1.0.14rc1.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc1.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc1.tar.bz2

and all the rest.

hunkiechan@HunkieChanUniverse:/usr/src/alsa$ $ sudo tar xjf alsa-driver-1.0.14rc3.tar.bz2
bash: $: command not found

now i get this one.. ^.. its in the desktop and i change the comand too sudo tar xjf alsa-driver-1.0.14rc*3*.tar.bz2

still doesnt work.. waht should i do ?

---

### Post by mikewhatever on 2007-03-15
Put/copy the files you downloaded in /usr/src/alsa and try again. You can't untar a file from /usr/src/alsa while the file is on the desktop.
I would also suggest training yourself with the terminal tutorial [http://www.linux.org.mt/node/49#N10025](http://www.linux.org.mt/node/49#N10025)

---

### Post by HunkieChan on 2007-03-16
> **mikewhatever said:**
> Put/copy the files you downloaded in /usr/src/alsa and try again. You can't untar a file from /usr/src/alsa while the file is on the desktop.
I would also suggest training yourself with the terminal tutorial [http://www.linux.org.mt/node/49#N10025](http://www.linux.org.mt/node/49#N10025)

i tried to copy it but it says i dont have the permission.. what should i do ?

---

### Post by HunkieChan on 2007-03-16
.. never mind bro.. im on it.. i owe you big time.. thanks alot..it not done yet though

---

### Post by HunkieChan on 2007-03-16
hey.. it worked.. yay.. dang. thanks alot.. thank you so much.. i wish you can stick with me and help me please ?.. how do i make my wirless work ? plase

---

### Post by mikewhatever on 2007-03-16
I am very glad it worked for you. About the wireless, as you can see, you have a Broadcom wireless card which may be a hard one to set up. It is beyond the scope of my very limited experience, much as I want to help you. This guide should get you started [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)
Also, search the forums Broadcom 4310 or for BCM4310.


*-network DISABLED
description: Wireless interface
product: BCM4310 UART
vendor: Broadcom Corporation
physical id: 0
bus info: pci@01:00.0
logical name: eth1
version: 01
serial: 00:1a:73:00:93:93
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
resources: iomemory:c3000000-c3003fff irq:233

---

### Post by HunkieChan on 2007-03-16
ok there is a slight problem.. my mic is not working and when ever i type my  mouse scrolls up and down , clicks at the point where i left it.. howdo i fix that.. thanks a lot again.. thanks a lot

---

### Post by HunkieChan on 2007-03-16
its too complicated...  i found everything but they say i have to uplug it before start it but its in my system.. how do i plug it.. ill do it when im more experienced meanwhile..  do you think i can get beryl with the graphics card i have ?

---

### Post by HunkieChan on 2007-03-16
when i do sudo update thingy i get this error

Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems

what should i do ?

---

