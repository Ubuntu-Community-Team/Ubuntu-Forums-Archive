---
title: "wireless not discovered"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by khelu on 2007-05-12
I need some help here please i cannot discover available wireless networks in my area. im using hp compaq nx9010. i also had some problem with the wireless with previous verson of wireless thats why i decided to go with windows again. I was hoping 7.04 will solve the problem. However it detects my wireless card but doesnt shows any wireless networks. Thanx in advance for helping me out.

---

### Post by jimrz on 2007-05-12
> **khelu said:**
> I need some help here please i cannot discover available wireless networks in my area. im using hp compaq nx9010. i also had some problem with the wireless with previous verson of wireless thats why i decided to go with windows again. I was hoping 7.04 will solve the problem. However it detects my wireless card but doesnt shows any wireless networks. Thanx in advance for helping me out.

please post your wifi card info (make/model/chipset). without this info it is not possible for anyone to help you find what you need. you might also try searching these forums for your wifi card type and see what, if any, problems others have encountered and possibly how they were able to overcome them.

---

### Post by khelu on 2007-05-17
ok sorry for late reply, been really busy these days, my wireless device is BCM4303 802.11b of broadcom corporation. i hope this helps to help me out still cannot figureout how to discover wireless access points even with the wireless radar.
thanx in advance once again.

---

### Post by yj09 on 2007-06-12
I also got problem with wireless on nx9010

lspci -v | less

00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0200
        Flags: medium devsel, IRQ 10
        Memory at d000a000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

lshw

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
             resources: iomemory:d000a000-d000afff irq:10

sudo lspci -n

00:00.0 0600: 1002:cbb2 (rev 02)
00:01.0 0604: 1002:7010
00:06.0 0401: 10b9:5451 (rev 02)
00:07.0 0601: 10b9:1533
00:08.0 0703: 10b9:5457
00:09.0 0280: 1260:3873 (rev 01)
00:0a.0 0607: 1217:6972
00:0b.0 0c03: 1106:3038 (rev 50)
00:0b.1 0c03: 1106:3038 (rev 50)
00:0b.2 0c03: 1106:3104 (rev 51)
00:0c.0 0c00: 104c:8026
00:10.0 0101: 10b9:5229 (rev c4)
00:11.0 0680: 10b9:7101
00:12.0 0200: 100b:0020
01:05.0 0300: 1002:4337

---

### Post by jfinkels on 2007-06-12
For the BCM43XX series drivers, check if your specific one is supported here: [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

If not, look here for more info: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

More info on supported hardware here: [http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

If you want help with a different driver, make your own thread.

---

### Post by rhydz on 2007-11-25
any update on this one did you get your wifi working.

i am on a nx9010 and have the same problem tried everything

---

