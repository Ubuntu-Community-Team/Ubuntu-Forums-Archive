---
title: "K73SV - Bluetooth not starting on boot"
date: 2011-08-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Santzes on 2011-08-15
I just bought ASUS K73SV, and instantly installed Ubuntu 11.04 next to the Win7 that came preinstalled.

Everything is working ok, except bluetooth won't start when I boot the computer to Ubuntu. If I boot to Win7, then restart back to Ubuntu, BT will work. If I reboot the computer while BT is working and boot back to Ubuntu, BT will work. If I halt the computer, even for a second, and boot straight to Ubuntu, BT does not work (Gnome Bluetooth Settings only has a button [Turn On Bluetooth] that does nothing)

I believe it's one of these:
> 

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: AzureWave Device 2c37
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at de200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

04:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
        Subsystem: ASUSTeK Computer Inc. Device 1851
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at dd800000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at a000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: atl1c
        Kernel modules: atl1c


---

### Post by sbraz on 2011-08-15
nope, those two are respectively your atheros wireless card and your gigabit ethernet card. :)

would you kindly run these commands from a terminal an post the results here:
```
uname -r
```
to determine your kernel version.

```
sudo rfkill unblock bluetooth
```
to attempt activating you bluetooth.

```
sudo dmesg |tail
```
to see what happens when you run the previous command.

---

### Post by Santzes on 2011-08-16
**uname -r**
> 2.6.38-10-generic
sudo rfkill unblock bluetooth, then **sudo dmesg|tail -n 20**
> 

[   17.851046] type=1400 audit(1313484191.207:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=814 comm="apparmor_parser"
[   17.856853] type=1400 audit(1313484191.217:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=814 comm="apparmor_parser"
[   17.857388] type=1400 audit(1313484191.217:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=814 comm="apparmor_parser"
[   17.915235] ppdev: user-space parallel port driver
[   17.981779] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.012104] atl1c 0000:04:00.0: irq 44 for MSI/MSI-X
[   18.107093] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.514890] Bluetooth: L2CAP ver 2.15
[   18.514893] Bluetooth: L2CAP socket layer initialized
[   18.557527] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.557532] Bluetooth: BNEP filters: protocol multicast
[   18.582407] Bluetooth: SCO (Voice Link) ver 0.6
[   18.582410] Bluetooth: SCO socket layer initialized
[   20.402035] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   20.739927] EXT4-fs (sda5): re-mounted. Opts: user_xattr,commit=0
[   23.208911] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   23.666859] EXT4-fs (sda5): re-mounted. Opts: user_xattr,commit=0
[   26.495194] Bluetooth: RFCOMM TTY layer initialized
[   26.495200] Bluetooth: RFCOMM socket layer initialized
[   26.495202] Bluetooth: RFCOMM ver 1.11


btw, rfkill list showed bluetooth as unblocked

---

### Post by joaquinx on 2011-08-16
#!/bin/bash -x

sudo killall bluetoothd

sudo bluetoothd

---

### Post by Santzes on 2011-08-16
> **joaquinx said:**
> #!/bin/bash -x

sudo killall bluetoothd

sudo bluetoothd

Did nothing. Also /etc/init.d/bluetooth stop -> start gave [ OK ] but did nothing.

---

### Post by cucisan on 2011-08-18
see k53sv family howto.. there is a fix for bluetooth - it may work for you

---

### Post by Santzes on 2011-08-18
> **cucisan said:**
> see k53sv family howto.. there is a fix for bluetooth - it may work for you

Thanks! That did the trick.

---

### Post by sbraz on 2011-08-18
> **cucisan said:**
> see k53sv family howto.. there is a fix for bluetooth - it may work for you
nice find. :)

> **Santzes said:**
> Thanks! That did the trick.
even nicer! :D

could you mark the topic as solved? :KS

---

