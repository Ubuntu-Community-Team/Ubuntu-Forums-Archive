---
title: "atheros a/b/g/n not recognized + other quirks"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by baterista on 2008-02-25
Hello, i'm returning to linux after a long hiatus,  and i'm glad to see that progress has been made. However, i've been having problems setting up wireless on my lenovo t60.

For starters, i've got the a/b/g/n card, and i get the following from
sudo lshw -C network

-->

 *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:e2:11:40
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.1.142 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ee000000-ee01ffff ioport:3000-301f irq:16
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:edf00000-edf0ffff irq:11
____________________________________________________________--

The ethernet interface works fine, I am using it right now. However, the wireless card appears to be unclaimed rather than disabled. I've tried installing madwifi, but ubuntu just doesnt recognize my card. I've read around the forums, but most of the other people's cards report as disabled rather than unclaimed. Any ideas?

Also, its a shame that beryl isnt doable on an ati x1400... is there a workaround? 

Thanks in advance,
baterista

---

### Post by mrsteveman1 on 2008-02-25
lshw isn't very helpful sometimes.

What does lspci say? If it doesn't say much try updating the pci ids first with update-pciids

---

### Post by fallsoff on 2008-02-25
Hi,
,My Dlink dwl g630 g-card has atheros drivers. I am in Gutsy and the o/s just picks the driver up as [what is it?] 'proprietary' I think. I get some nag popups about the driver, but it works better in Ubuntu than in XP, where its .reg component takes 100% cpu. I had an Ubuntu Kwifi app that worked even better with that driver. That came with a magazine coverdisk Ubuntu setup from Linux Format mag.
Anyway, my 2 bits on Atheros__sorry no solutions here.
Best,
fallsoff

---

### Post by baterista on 2008-02-26
I updated the pc id's and now lspci shows the atheros abgn as network controller:
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

However, the hardware infromation in system>preferences still shows it as unknown.

any tips?

---

