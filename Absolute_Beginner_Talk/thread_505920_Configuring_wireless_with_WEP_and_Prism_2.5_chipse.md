---
title: "Configuring wireless with WEP and Prism 2.5 chipset"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by aldehyde on 2007-07-20
I just installed Ubuntu on my old laptop and am amazed at how awesome it is, everything has worked straight from install with the exception of wireless internet. Wired works fine, and I've been trying a few different methods (wpa supplicant and ndiswrapper) but so far nothing has worked.

Its an HP ze4365us and here is the information about the wlan adapter:

00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 
01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0200
        Flags: medium devsel, IRQ 10
        Memory at d0401000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

also,

```
alex@planck:~$ sudo lshw -C Network
  *-network:0 DISABLED    
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=64 link=no multicast=yes
       resources: iomemory:d0401000-d0401fff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:59:10:ac
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.102 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:8c00-8cff iomemory:d0008000-d0008fff irq:11

```

why does it say disabled? just because im using the other connection?

I have used linux before, but never enough to really know what I'm doing. When I manually configure my network properties it lists both connections as wired, although the first is "Wired connection (wlan0)" and I am connected through eth0 via a wired connection.

Has anyone been able to configure this correctly? I would really love some help, I need to replace my battery and right now whenever I jiggle the laptop it restarts--so not having to also be tethered to the router would be great.

---

### Post by lsutiger on 2007-07-21
Have you tried to enable it through the network admin tool (system-->Admin-->network)?

---

### Post by aldehyde on 2007-07-22
Yeah when I check the wlan0 adapter it doesn't detect any SSIDs and if I manually add the info it just sits there trying to connect.

edit: actually when I configure it and set it to use dhcp it connects as a wired connection. I initially tried using the broadcom drivers (thought that was my chipset, but all the commands say Prism 2.5), what is the name of the prism driver to use with ndiswrapper?

---

### Post by aldehyde on 2007-07-22
Oh man I'm so close. After finding this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989)

I tried running the following commands:

$ sudo modprobe -r orinoco_pci
$ sudo modprobe -r hostap_pci
$ sudo modprobe -r prism2_pci
$ sudo modprobe orinoco_pci

My network adapter now shows it correctly as a wireless connection and I can add all of my information. It still isn't working, but I'm getting closer!

---

### Post by aldehyde on 2007-07-22
haha okay POSTING WIRELESSLY!!! Not sure exactly what did it, but blacklisting those drivers and then messing around fixed it.

Only problem, somehow I removed my network status indicator, how can I get it back?

---

### Post by plungerman on 2007-07-28
thanks aldehyde, i have compaq presario 2500 with a prism card that exhibited the same behaviour.  i followed your procedure and now everything works well.

---

### Post by airkoold on 2007-08-02
my nx9000 has prism 2.5 wlan and after 1 night of struggle I can also post wirelessly \\:D/

thanks !

---

### Post by airkoold on 2007-08-05
my problem now is that the pc does not keep the setting

how can I run this command everytime during startup?

---

