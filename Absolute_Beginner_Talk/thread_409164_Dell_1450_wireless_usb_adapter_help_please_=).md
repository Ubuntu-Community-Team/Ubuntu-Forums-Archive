---
title: "Dell 1450 wireless usb adapter help please =)"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by firefly2005 on 2007-04-14
Hey guys =) Ive just installed ubuntu through the alternative disk, as i am using an ATI x600 graphics card, but i need to get my wireless card working =(

ive read thousands upon thousands of posts but do not have a clue what they are on about =) i have alien, as the driver disk had some drivers for a different version of linux. Is there some way of installing them? and if not is there any other methods?

there is alot of posts about ndiswrapper which i have downloaded yet havnt a clue on what to do with it =) 

im sorry if this has already been answered 

firefly =D

*Sorry guys, i the wireless card is the "Dell 1450 wireless usb adapter" if you havnt guessed by the title of the post =)

---

### Post by caffienefree on 2007-04-14
Please enter this command into the terminal, and post the result.

lspci -v|grep 'Network'

---

### Post by firefly2005 on 2007-04-14
ok ive typed it in and it did nothing but move to the next line down =/ im guessing thats not good? thanks for you help =)

---

### Post by jjalocha on 2007-04-14
OK, then just type the following, and post the whole output:

```

$ lspci

```

---

### Post by caffienefree on 2007-04-14
Sorry, I'm not still fully awake. Actually, I looked up your problem, I don't think you need it. Can you get the windows drivers from dell? (i.e the .inf and .sys file for that adapter)

Also, could you please post the output of **lshw -C network**

---

### Post by firefly2005 on 2007-04-14
the output to lspci is:
tommy@burtha:~$ lspci

00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)

00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]

01:00.1 Display controller: ATI Technologies Inc Radeon X600(RV380)

03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

sorry it took so long =) the second output is coming shortly:D

---

### Post by firefly2005 on 2007-04-14
tommy@burtha:~$ sudo lshw -C network

*-network DISABLED 

description: Ethernet interface

product: 82801G (ICH7 Family) LAN Controller

vendor: Intel Corporation

physical id: 8

bus info: pci@03:08.0

logical name: eth0

version: 01

serial: 00:12:3f:b7:18:3b

size: 10MB/s

capacity: 100MB/s

width: 32 bits

clock: 33MHz

capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation

configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s

resources: iomemory:efbfb000-efbfbfff ioport:ccc0-ccff irq:201

*-network DISABLED

description: Wireless interface

physical id: 1

logical name: eth1

serial: 00:3d:b4:00:00:00

capabilities: ethernet physical wireless

configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b




thanks again for your help guys =/

---

### Post by caffienefree on 2007-04-14
Go to system>administration>network. Select wireless, click properties. Is it enabled?

---

### Post by firefly2005 on 2007-04-14
wireless network is yes, but i dont think i have installed any of the drivers for my wireless card =/ the disk came with the drivers for both linux and windows, the linux drivers where in an archive which i tried to open but it wouldnt let me =/ so i searched the problem and found they were for redhat and i needed alien. But being completely new to the whole linuxing world i havnt got a clue how to install them or even if its possible

the other option that i found others trying to go down is using ndiswrapper =/ but that looks way complcated! :confused: specially when im more knowledgable with the easiness of DOS

---

### Post by caffienefree on 2007-04-14
ndiswrapper is actually very easy. You just need the windows drivers for your device, the .inf and .ys, that you can find by searching google. in fact, you can do it from a gui too. Do you have a wired connection on your computer? if so, open synaptic, make sure you have the universe repository enabled, then search for ndisgtk. After installing that, open a terminal and type **sudo ndisgtk**. Then you can use ndisgtk to browse to wherever you saved the .inf file and install.

---

### Post by firefly2005 on 2007-04-14
Awsome, but i dont have a wired connection =/ ive installed ndiswrapper =D and found the drivers. then used ```
sudo ndiswrapper -i /home/tommy/DELLNIC.inf
``` but the command ndiswrapper -l shows "dellnic invalid driver" =/ im sure it is compatable with ndiswrapper =s is it something im doing wrong? thanks for the help

---

### Post by caffienefree on 2007-04-14
Hmm. What's the .sys file?  prisma02.sys?

---

### Post by firefly2005 on 2007-04-14
yer thats the cookie! =D

---

### Post by firefly2005 on 2007-04-23
:(  Hmmmmm just installed 7.04 cant get it to work there neither =/ ive loaded the Inf and sys files into ndiswrapper and everything, my hardware isnt detected. Does anyone have a solution? :confused: :confused: :confused:

---

