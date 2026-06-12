---
title: "Installing Netgear WG311 v3 on Kubuntu 6.06"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by reeksy on 2006-09-20
Hi

I'm stuck! Ive done a lot of searching but i'm a beginner to linux so im completely lost.

How do i install the Netgear Wireless PCI Adapter WG311 v3 on Kubuntu?

I'm aware that i have to install a package from the Adept Manager but i'm unsure exactly which one to install?

Ive searched [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") but im unsure what to do with the information?

Jon

---

### Post by nickpaton on 2006-09-20
Hi Reeksy and welcome to the forums!

With the card is plugged in can you send me the outputs, using Terminal, from 

> lspci

and

> iwconfig

and

> lshw -C network

All three give information about your system and will identify the chipset of the card.

---

### Post by reeksy on 2006-09-21
Thanks for the reply!

Here are my results:


ndis
> 
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bri                                                              dge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Br                                                              idge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller                                                               (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller                                                               (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev                                                               a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound                                                               Controller (rev a0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa                                                              st Ethernet (rev 90)
0000:00:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Liberta                                                              s] 802.11b/g Wireless (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 95                                                              50]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Se                                                              condary)

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.


lshw -C network
> WARNING: you should run this program as super-user.
  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth0
       version: 90
       serial: 00:0a:e6:33:8b:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 multicast=yes
       resources: ioport:cc00-ccff iomemory:cfffd000-cfffdfff irq:11
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: b
       bus info: pci@00:0b.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       resources: iomemory:cffe0000-cffeffff iomemory:cffb0000-cffbffff irq:11

Does this help!?

Jon

---

### Post by nickpaton on 2006-09-21
Thanks for that Jon

It tells me that you have a Marvell chip and is at least recognised.

I have found the following wiki which walks you through using ndiswrapper.

[http://www.jimbo7.com/wiki/index.php?title=WG311v3]("http://www.jimbo7.com/wiki/index.php?title=WG311v3")

The first thing you will have to do is to find the WG311 windows drivers, and copy into your Ubu home folder.

Note that the wiki states that you should be looged in as root.  The command for Ubu is

```
sudo su
```

or simply put

```
sudo
```

in front of every command

Good luck, take a deep breath and give it a go!

---

### Post by reeksy on 2006-09-21
Thanks nickpaton

I think tonight might be a late one...!

---

### Post by reeksy on 2006-10-08
Hi again!

OK - so I turned my back on Linux around two weeks ago, but I’m back; with renewed optimism!

I failed badly whilst trying to install my wireless network card in the sense that I came completely lost at the first hurdle! Nothing much has changed since then except I’m now even more determined to make the switch from Windows to Linux.

Ive downloaded and compiled from source the latest NdisWrapper however I’m unsure which step to take next! It says [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation"): 
```
Go to the source-directory and run 'make distclean' and 'make'. As root, run 'make install'. This should compile and install both the kernel module and the userspace utilities
```

But I can’t seem to run either of these three commands. I get the following error:
```

bash: make: command not found

```

Can anyone help me from here!?

Jon

---

### Post by reeksy on 2006-10-09
Can anyone throw me in the right direction here!?!

---

### Post by gbell12 on 2006-10-21
```

bash: make: command not found

```

For some reason, Ubuntu doesn't install the stock tools you need to build from source.  Talk about ](*,) 

Install these and you should be happy:

apt-get install make gcc gcc-dev manpages-dev autoconf automake libtool flex bison gcc-doc g++

---

