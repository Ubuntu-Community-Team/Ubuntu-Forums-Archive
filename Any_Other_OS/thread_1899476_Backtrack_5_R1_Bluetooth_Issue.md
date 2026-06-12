---
title: "Backtrack 5 R1 Bluetooth Issue"
date: 2011-12-23
forum: Any Other OS
---

### Post by Kchymet on 2011-12-23
Recently, I installed KDE Backtrack 5 R1 (64 bit) on my laptop, and so far I'm liking it. I have one small issue though, and that's that I can't seem to connect my Dell Bluetooth Travel Mouse. I've worked through the applet that appears when I turn on the Bluetooth daemon, but then I get an error when I attempt to establish a connection. The error reads as follows:
```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "<string>", line 2, in CreateDevice
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/DBusService.py", line 135, in CreateDevice
    agent = TempAgent(self.Applet.Plugins.StatusIcon, agent_path, time)
  File "/usr/lib/python2.6/dist-packages/blueman/main/applet/BluezAgent.py", line 255, in __init__
    CommonAgent.__init__(self, status_icon, path)
  File "/usr/lib/python2.6/dist-packages/blueman/main/applet/BluezAgent.py", line 52, in __init__
    Agent.__init__(self, path)
  File "/usr/lib/python2.6/dist-packages/blueman/bluez/Agent.py", line 68, in __init__
    dbus.service.Object.__init__(self, dbus.SystemBus(), obj_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/blueman/agent/temp/000761CBE92F': there is already a handler"

```
Some additional info:
-The laptop is a Dell Inspiron 1525 with no screen (running GUI through VGA with no problems, though I don't see how this is relevant to Bluetooth)
-Installing jockey-gtk makes everything go to hell when it prompts me to use Broadcom proprietary drivers
-WiFi and ethernet worked on boot. It seems to be unrelated to the network card.
-I can detect the bluetooth mouse (it's listed with the correct MAC address), but I cannot connect to it.
-lspci and lsusb return as follows. It appears I have Dell Computer Corp. Wireless 355 Bluetooth:
```
root@bt:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
root@bt:~# lsusb
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jdimstrnate on 2012-01-22
I am having the same issue.  

I think its because it created a temp pairing of the device and now you are basically trying to "do it again" and its telling you to knock it off because its already paired.  
If thats the case I dont know why its not working because I cant get the pointer to move.

You can try and go to the directory listed at the end of the error message and delete the folder.  youll notice that the folder name should be the same as your BT device HW ADDR.

Driving me nuts.

---

