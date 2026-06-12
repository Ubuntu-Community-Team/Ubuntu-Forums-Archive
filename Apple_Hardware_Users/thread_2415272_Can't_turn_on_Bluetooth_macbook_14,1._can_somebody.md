---
title: "Can't turn on Bluetooth macbook 14,1. can somebody help?"
date: 2019-03-23
forum: Apple Hardware Users
---

### Post by david1893 on 2019-03-23
It's a couple days after i successfully installed ubuntu on My New Macbook Pro 2017.

got everything (almost. no sound driver) working except one thing. the bluetooth.

i checked the terminal and i have the following error:
___________________________________________________________________________________________________________
david1893@david1893-MacBookPro:~$ uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
4.19.30-041930-generic
Bus 004 Device 003: ID 05e3:0749 Genesys Logic, Inc. 
Bus 004 Device 002: ID 05e3:0626 Genesys Logic, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 015: ID 05ac:1460 Apple, Inc. 
Bus 001 Device 014: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 001 Device 013: ID 05ac:100f Apple, Inc. 
Bus 001 Device 005: ID 1d57:0008 Xenta 
Bus 001 Device 016: ID 1a2c:2d43 China Resource Semico Co., Ltd 
Bus 001 Device 003: ID 1d5c:7102  
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4350 802.11ac Wireless Network Adapter [14e4:43a3] (rev 05)
    Subsystem: Apple Inc. BCM4350 802.11ac Wireless Network Adapter [106b:0170]
    Kernel driver in use: brcmfmac
    Kernel modules: brcmfmac
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
hci0:    Type: Primary  Bus: UART
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:28 acl:0 sco:0 commands:4 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 


[    0.113082] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.135271] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    2.030303] thunderbolt 0000:06:00.0: starting ICM firmware
[    2.074337] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[   15.479097] Bluetooth: Core ver 2.22
[   15.479111] Bluetooth: HCI device and connection manager initialized
[   15.479114] Bluetooth: HCI socket layer initialized
[   15.479116] Bluetooth: L2CAP socket layer initialized
[   15.479120] Bluetooth: SCO socket layer initialized
[   15.502323] Bluetooth: HCI UART driver ver 2.3
[   15.502325] Bluetooth: HCI UART protocol H4 registered
[   15.502325] Bluetooth: HCI UART protocol BCSP registered
[   15.502337] Bluetooth: HCI UART protocol LL registered
[   15.502337] Bluetooth: HCI UART protocol ATH3K registered
[   15.502345] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   15.502365] Bluetooth: HCI UART protocol Intel registered
[   15.502390] Bluetooth: HCI UART protocol Broadcom registered
[   15.502397] Bluetooth: HCI UART protocol QCA registered
[   15.502397] Bluetooth: HCI UART protocol AG6XX registered
[   15.502398] Bluetooth: HCI UART protocol Marvell registered
[   15.688959] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac4350c2-pcie.txt failed with error -2
[   15.949652] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac4350c2-pcie.clm_blob failed with error -2
[   15.949952] brcmfmac: brcmf_c_preinit_dcmds: Firmware: BCM4350/5 wl0: Nov 26 2015 03:48:57 version 7.35.180.133 (r602372) FWID 01-c45b39d6
[   16.430424] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.430426] Bluetooth: BNEP filters: protocol multicast
[   16.430429] Bluetooth: BNEP socket layer initialized
[   17.617067] Bluetooth: hci0: command 0xfc18 tx timeout
[   25.649135] Bluetooth: hci0: BCM: failed to write update baudrate (-110)
[   25.649146] Bluetooth: hci0: Failed to set baudrate
[   27.665343] Bluetooth: hci0: command 0x0c03 tx timeout
[   35.889080] Bluetooth: hci0: BCM: Reset failed (-110)
[ 9822.636561] Bluetooth: hci0: command 0xfc18 tx timeout
[ 9830.668459] Bluetooth: hci0: BCM: failed to write update baudrate (-110)
[ 9830.668462] Bluetooth: hci0: Failed to set baudrate
[ 9832.688497] Bluetooth: hci0: command 0x0c03 tx timeout
[ 9833.987762] Bluetooth: hci0: BCM: Reset failed (-4)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

is there somebody who knows the error and has a fix/knows how to fix this?

Anyway thanks in mind :P

David

---

### Post by alexzhang7801 on 2019-03-28
same issue. Mark

---

