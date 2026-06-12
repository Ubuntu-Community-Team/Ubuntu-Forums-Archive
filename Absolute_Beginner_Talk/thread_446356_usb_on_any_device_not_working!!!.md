---
title: "usb on any device not working!!!"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Lucius Demon on 2007-05-16
ok here's the problem: im on fiesty fawn with an msi laptop. i have an ipod and camera id like to connect WITHOUT any problems or editing the boot loader (that comes out to be a disaster). if you know a command line or two, i would appreciate it since i am in dire need to get my work done.

---

### Post by mahy on 2007-05-17
sudo mount -t [filesystem type] [device name] [mount point]

example for my usb key would be:

sudo mount -t vfat /dev/sdb1 /mnt/usb

If your hard drives are all ATA, then use /dev/sda1 as a device name

---

### Post by Lucius Demon on 2007-05-24
ive tried the mount commands before but they are of no use. when i do the command dmesg it says

> [  522.498094] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  522.518413] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.518429] hub 3-0:1.0: hub_port_status failed (err = -32)
[  522.592615] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.592626] hub 3-0:1.0: hub_port_status failed (err = -32)
[  522.666674] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.666690] hub 3-0:1.0: hub_port_status failed (err = -32)
[  522.740723] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.740727] hub 3-0:1.0: hub_port_status failed (err = -32)
[  522.814780] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.814786] hub 3-0:1.0: hub_port_status failed (err = -32)
[  522.814788] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  522.835103] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.835107] hub 3-0:1.0: hub_port_status failed (err = -32)
[  522.909005] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.909010] hub 3-0:1.0: hub_port_status failed (err = -32)
[  522.983214] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  522.983219] hub 3-0:1.0: hub_port_status failed (err = -32)
[  523.057142] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  523.057148] hub 3-0:1.0: hub_port_status failed (err = -32)
[  523.131163] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  523.131170] hub 3-0:1.0: hub_port_status failed (err = -32)
[  523.131174] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?


but say the truth, the usb cables and the four 2.0 speed usb ports are brand new and tested.

---

