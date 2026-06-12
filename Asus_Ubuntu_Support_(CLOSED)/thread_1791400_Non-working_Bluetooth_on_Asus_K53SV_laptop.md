---
title: "Non-working Bluetooth on Asus K53SV laptop"
date: 2011-06-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Triton Yurin on 2011-06-26
Hi everyone,
I can't get Bluetooth working on my Asus K53SV laptop.
Taking off the battery, I discovered that an Atheros AR5B195 Combo card is installed there.
According to Google, it consists of AR9285(wlan) and AR3011(bluetooth).
I'm using Ubuntu Natty (amd64) with kernel 2.6.38-10 installed.
Just need Bluetooth to get my BT mouse working.
Here's output of some commands about system and bluetooth.

```

**lsusb**
Bus 002 Device 003: ID 09da:8090 A4 Tech Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 13d3:5710 IMC Networks 
Bus 001 Device 003: ID 13d3:3304 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

**lspci**
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```
```
**hciconfig -a**
hci0:   Type: BR/EDR  Bus: USB
   BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
   DOWN 
   RX bytes:0 acl:0 sco:0 events:0 errors:0
   TX bytes:66 acl:0 sco:0 commands:21 errors:1

```
```
**sudo hciconfig hci0 up**
Can't init device hci0: Connection timed out (110)

```
```
**rfkill list bluetooth**
0: hci0: Bluetooth
   Soft blocked: no
   Hard blocked: no

```

---

### Post by Triton Yurin on 2011-06-27
Well, lets make it easier.
How can I make Atheros AR3011 Bluetooth chip working on Ubuntu 11.04?

---

### Post by joebarker182 on 2011-08-14
yes... same problem here...


bump

bump

---

### Post by Qaranthir on 2011-08-15
I've got the same laptop (ASUS K53SV) with the same combo-card. 
I got it working with the dkms-driver on Ubuntu 11.04 64bits (kernel 2.6.38-10-generic):
1. download the driver:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb)
2. install the driver:
sudo dpkg -i ar3011-dkms_1.1ryu2.3_all.deb dell-laptop-dkms_1.4_all.deb
3. Check the installation:
run "dkms status" to see if there are the following info:
ar3011-dkms, 1.1ryu2.3, 2.6.38-10-generic, x86_64: installed (or similar)

After a reboot, the bluetooth icon should appear and indicate that bluetooth is working.

---

### Post by jfgencarnacao on 2012-06-12
The link to the file doesn't work anymore. Does anyone have this file or another workaround for this problem?

---

