---
title: "Device usage at 100% on MacBook Air 4,1"
date: 2012-07-02
forum: Apple Hardware Users
---

### Post by Kallun on 2012-07-02
Hello guys :)

I'm running Arch Linux, however, felt that the Ubuntu community may be able to help as there seem to be quite a few active members using Ubuntu on the MacBook Air.

I have an awful problem with battery consumption on my MacBook Air. The battery depletes extremely fast, only really giving me about two hours battery life.

Here's the device usage report from PowerTOP:

```

The battery reports a discharge rate of 16.6 W

              Usage     Device name
            100.0%        USB device: Apple Internal Keyboard / Trackpad (Apple Inc.)
            100.0%        Display backlight
            100.0%        Display backlight
            100.0%        Radio device: btusb
            100.6 pkts/s  Network interface: wlan0 (wl)
            100.0%        Radio device: wl
            100.0%        USB device: usb-device-0424-2513
            100.0%        USB device: EHCI Host Controller
            100.0%        Audio codec hwC0D3: Intel
              5.2%        CPU use
              0.0%        USB device: EHCI Host Controller
              0.0%        USB device: UHCI Host Controller
              0.0 ops/s   GPU
              0.0%        USB device: usb-device-0424-2513
              0.0%        USB device: UHCI Host Controller
              0.0%        USB device: BRCM20702 Hub (Apple Inc.)
              0.0%        USB device: Bluetooth USB Host Controller (Apple Inc.)
              0.0%        Audio codec hwC0D0: Cirrus Logic
              0.0%        USB device: FaceTime Camera (Built-in) (Apple Inc.)
            100.0%        PCI Device: Intel Corporation Device 151a
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1
            100.0%        PCI Device: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller
            100.0%        PCI Device: Intel Corporation Device 151a
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5
            100.0%        PCI Device: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2
            100.0%        PCI Device: Intel Corporation Device 151a
            100.0%        PCI Device: Intel Corporation 2nd Generation Core Processor Family DRAM Controller
            100.0%        PCI Device: Broadcom Corporation BCM43224 802.11a/b/g/n
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller
            100.0%        PCI Device: Intel Corporation Device 151a
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
              0.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1

```

As you can see, there's a fair few devices with 100% usage! So this is most likely the culprite.

I've added some commands to my rc.local to help with consumption, although they have helped a little bit, ptop is still reporting the above device status'.

Here's my rc.local:

```
#!/bin/bash
#
# /etc/rc.local: Local multi-user startup script.
#
# - CPU Scaling (on demand scaling governor for all CPU's
for i in `find /sys/devices/system/cpu/*/cpufreq/scaling_governor`; do echo ondemand > $i; done;

# - CPU Scheduler
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings;

# - Intel HDA
echo 1 > /sys/module/snd_hda_intel/parameters/power_save;

# - Laptop Mode
echo 5 > /proc/sys/vm/laptop_mode;

# - NMI Watchdog (turned off)
echo 0 > /proc/sys/kernel/nmi_watchdog;

# - Runtime Power Management
for i in `find /sys/devices/*/power/control`; do echo auto > $i; done;

# - SATA Active Link Powermanagement
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy;

# - USB Autosuspend (after 2 secs of inactivity)
for i in `find /sys/bus/usb/devices/*/power/control`; do echo auto > $i; done;
for i in `find /sys/bus/usb/devices/*/power/autosuspend`; do echo 2 > $i; done;

# - Device Power Management
echo auto | tee /sys/bus/i2c/devices/*/power/control > /dev/null;
echo auto | tee /sys/bus/pci/devices/*/power/control > /dev/null;

# - Set the VM dirty writeback time to 15 seconds
echo '1500' > '/proc/sys/vm/dirty_writeback_centisecs';

# - Enable wifi Power Management
iwconfig wlan0 power on

```

Here's the modules I load on startup:
```

DAEMONS=(dbus slim syslog-ng crond acpid laptop-mode cpufreq_userspace acpi-cpufreq granola wl wicd alsa)

```

And here's my bootline for Grub2:

```

linux /boot/vmlinuz-linux root=UUID=22843656-47cd-428f-9e27-0af678c96a06 rootflags=,relatime,data=ordered rootfstype=ext4 ro logo.nologo quiet

```

I've also added the 'i915.i915_enable_rc6=1' boot option along with pcie_aspm=force, however have not seen any significant improvements :(


Any advice on this at all is greatly appreciated!

---

