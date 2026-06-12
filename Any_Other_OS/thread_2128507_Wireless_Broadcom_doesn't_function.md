---
title: "Wireless Broadcom doesn't function"
date: 2013-03-23
forum: Any Other OS
---

### Post by nick85x on 2013-03-23
Hello guys,
I'm so excited for this new operating system (Linux), I come from Windows OS, but now I'm really satisfied.
Please have patience with me, because I'm still learning the basics of Linux.
I have a small/big problem. The wireless does not work.
I followed this little guide (which also corresponds to the one mentioned, but to no avail) :
[http://community.linuxmint.com/tutorial/view/796](http://community.linuxmint.com/tutorial/view/796)
 [IMG]http://forums.linuxmint.com/images/smilies/icon_sad.gif[/IMG]  
Because it corresponds exactly to my wireless card:
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
that is to say:
sudo apt-get install firmware-b43-installer
gave error, then I gave:
sudo apt-get install firmware-b43-lpphy-installer
and now he seems to see the wifi card, based on what iwconfig says:
wlan0....IEEE 802.11bg..ESSID : off/any
..........Mode:Managed..Access Point: Not-Associated...Tx-Power=0 dBm   
..........Retry  long limit:7...RTSthr: off...Fragment thr: off
..........Power Management: on
I also gave him:
sudo lshw -C network
..*-network               
.......description: Network controller
.......product: BCM4312 802.11b/g LP-PHY
.......vendor: Broadcom Corporation
.......physical id: 0
.......bus info: pci@0000:04:00.0
.......version: 01
.......width: 64 bits
.......clock: 33MHz
.......capabilities: pm msi pciexpress bus_master cap_list
.......configuration: driver=b43-pci-bridge latency=0
.......resources: irq:18 memory:9c200000-9c203fff
..*-network
.......description: Ethernet interface
.......product: RTL8111/8168B PCI Express Gigabit Ethernet controller
.......vendor: Realtek Semiconductor Co., Ltd.
.......physical id: 0
.......bus info: pci@0000:05:00.0
.......logical name: eth0
.......version: 02
.......serial: 00:1e:ec:bb:0f:de
.......size: 100Mbit/s
.......capacity: 1Gbit/s
.......width: 64 bits
.......clock: 33MHz
.......capabilities:  pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp  mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
.......configuration:  autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI  duplex=full ip=192.168.2.100 latency=0 link=yes multicast=yes port=MII  speed=100Mbit/s
.......resources: irq:48 ioport:3000(size=256) memory:96010000-96010fff memory:96000000-9600ffff memory:96020000-9602ffff
..*-network DISABLED
.......description: Wireless interface
.......physical id: 2
.......logical name: wlan0
.......serial: 00:21:00:68:52:8f
.......capabilities: ethernet physical wireless
.......configuration:  broadcast=yes driver=b43 driverversion=3.5.0-17-generic firmware=N/A  link=no multicast=yes wireless=IEEE 802.11bg
I copied the complete answer of dmesg in dmesg.txt and is uploaded here: [http://www.fileconvoy.com/dfl.php?id=g3609ff1c7639844a999250191f0cddbd722747744](http://www.fileconvoy.com/dfl.php?id=g3609ff1c7639844a999250191f0cddbd722747744)
My computer is an Hp pavilion dv4-1190el and I installed Linux Mint 14 Xfce 32bit all codecs (so it's an ubuntu like)(I use Mint because unbuntu, doesn't starts, all release, lots off error, I don't know why, anyway).
Thanks in advance, best regards.
Antony

---

### Post by Perfect Storm on 2013-03-24
Moved to Other OS/Distro Talk.

---

### Post by mamamia88 on 2013-03-24
This may sound crazy but did you try rebooting after installing the package? You may have installed the driver but it won't load until you restart sometimes.

---

### Post by nick85x on 2013-03-24
Thanks, "mamamia88", but the rebooting was the first think I have done.

To show you, I tryed:
ciao@HP-Pavilion ~ $ dmesg | grep Broadcom
[   25.933613] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   26.001752] Broadcom 43xx driver loaded [ Features: PNL ]
ciao@HP-Pavilion ~ $ lspci -nn | grep -i net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
ciao@HP-Pavilion ~ $ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ciao@HP-Pavilion ~ $ dmesg | grep error
[   24.703613] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   25.512455] ACPI: Marking method HWMC as Serialized because of AE_ALREADY_EXISTS error
[   25.512466] ACPI: Marking method WMAD as Serialized because of AE_ALREADY_EXISTS error

What you think happen if i give this:
sudo apt-get install pciutils
sudo update-pciids
update-pciids fetches the current version of the pci.ids file from the primary distribution site and installs it. This utility requires curl, wget or lynx to be installed.
Because I found it written that a person who has launched sudo update-pciids then after some time had problems with the wireless device and also with others devices.
For me, this here is the last resort. I do not know where else to go beat my head. Please be understanding for me.

Thanks in advance.
Antony

---

### Post by Perfect Storm on 2013-03-24
> For "Artificial Intelligence": Where I can go? I had open a thread on linux mint forum, but no one helped me, answered. For me, this here is the last resort. I do not know where else to go beat my head. Please be understanding for me.

It's a standard message when the mods are moving threads. 
You're welcome to use our forums, but note that non-ubuntu issues/questions are going to be posted in our 'Other OS/distro Talk' forum.

regards
A.I.

---

### Post by nick85x on 2013-03-24
Thanks guys,
Now the wireless is fine.
I solved it! Looks here:
[http://forums.linuxmint.com/viewtopic.php?f=53&t=129309](http://forums.linuxmint.com/viewtopic.php?f=53&t=129309)
Greetings
Antony alias nick85x

---

