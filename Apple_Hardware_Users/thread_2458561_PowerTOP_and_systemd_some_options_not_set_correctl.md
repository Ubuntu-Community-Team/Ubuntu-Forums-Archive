---
title: "PowerTOP and systemd: some options not set correctly though present"
date: 2021-02-27
forum: Apple Hardware Users
---

### Post by a.borque on 2021-02-27
Hello!
I have installed Budgie 20.04.2 on my MBP 8,2 (MacBook Pro 15, late 2011)

To save energy I have used PowerTOP and implemented the suggestions using systemd (see end of my post).
But though they are configured in systemd, when I log into my system some tweaks are not set according to another run of powertop executed afterwards.
I tried to change the sequence of the tweaks or execute powertop --auto-tune instead of the single echo-lines. The result is always the same.

What am I making wrong?
Thanks
A.Borque

Missing tweaks after reboot:
```

"echo 'min_power' > '/sys/class/scsi_host/host4/link_power_management_policy';" 
"echo 'min_power' > '/sys/class/scsi_host/host5/link_power_management_policy';" 
"echo 'min_power' > '/sys/class/scsi_host/host3/link_power_management_policy';" 
"echo 'min_power' > '/sys/class/scsi_host/host1/link_power_management_policy';" 
"echo 'min_power' > '/sys/class/scsi_host/host2/link_power_management_policy';" 
"echo 'min_power' > '/sys/class/scsi_host/host0/link_power_management_policy';" 

"echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs';" 

"echo 'auto' > '/sys/bus/usb/devices/1-1.2/power/control';" 
"echo 'auto' > '/sys/bus/usb/devices/2-1.1/power/control';"

```

Contents of powertop.service:
```

[Unit]
Description=PowerTOP auto tune

[Service]
Type=oneshot
RemainAfterExit=yes

ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-8/device/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-14/device/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-7/device/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-13/device/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-11/device/power/control';"
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-9/device/power/control';"  
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-10/device/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/i2c/devices/i2c-12/device/power/control';" 

ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/usb/devices/1-1.2/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/usb/devices/2-1.1/power/control';"
 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/block/sda/device/power/control';" 

ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/ata3/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/ata4/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/ata1/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/ata2/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/ata5/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/ata6/power/control';" 

ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:00:16.0/power/control';" 
ExecStart=/bin/sh -c "echo 'auto' > '/sys/bus/pci/devices/0000:01:00.0/power/control';" 

ExecStart=/bin/sh -c "echo 'enabled' > '/sys/class/net/wlp3s0/device/power/wakeup';"  
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/class/net/enp2s0f0/device/power/wakeup';"
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/usb3/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/2-1/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/usb1/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/1-1.1/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/1-1/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/usb4/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/2-1.1/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/1-1.1.3/power/wakeup';" 
ExecStart=/bin/sh -c "echo 'enabled' > '/sys/bus/usb/devices/usb2/power/wakeup';"

ExecStart=/bin/sh -c "echo 'min_power' > '/sys/class/scsi_host/host4/link_power_management_policy';" 
ExecStart=/bin/sh -c "echo 'min_power' > '/sys/class/scsi_host/host5/link_power_management_policy';" 
ExecStart=/bin/sh -c "echo 'min_power' > '/sys/class/scsi_host/host3/link_power_management_policy';" 
ExecStart=/bin/sh -c "echo 'min_power' > '/sys/class/scsi_host/host1/link_power_management_policy';" 
ExecStart=/bin/sh -c "echo 'min_power' > '/sys/class/scsi_host/host2/link_power_management_policy';" 
ExecStart=/bin/sh -c "echo 'min_power' > '/sys/class/scsi_host/host0/link_power_management_policy';" 

ExecStart=/bin/sh -c "echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs';" 

[Install]
WantedBy=multi-user.target

```

---

### Post by a.borque on 2021-02-28
I noticed that tlp is also installed which overwrites some autotunes settings. Uninstalling this solved the problem.

---

