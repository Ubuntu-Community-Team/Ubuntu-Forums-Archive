---
title: "Hot SSD on MacBook Air (mid 2013) with Ubuntu 22.04.1"
date: 2022-11-09
forum: Apple Hardware Users
---

### Post by igloigabor on 2022-11-09
Dear Members,

I've installed Ubuntu 22.04.1 LTS on my MacBook Air (mid 2013).
So far Ubuntu is working quite well on this hardware.

However I noticed that the internal SSD is 10-15 Celsius warmer than it is under macOS Big Sur.
It is constantly between 65-70 degrees (sometimes even above 70C) depending on system load, whilst it is 45-55 under Big Sur.

Physical environment and hardware is the exactly the same with OSX and with Ubuntu.

I am using smartctl to obtain temperature data and also tried lm-sensors with the drivetemp kernel module, the results are the same both ways.

So far I have experienced with these things to lower SSD temps:

- GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=!Darwin"
- GRUB_CMDLINE_LINUX_DEFAULT="libata.force = noncq"

- hdparm -B 128 /dev/sda

- Power Saver power mode in Gnome

- apt install mbpfan and setting up mbp.conf, starting the service

- echo "ondemand" | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

- write kernel.nmi_watchdog = 0 to /etc/sysctl.d/disable_watchdog.conf

Could you help me where to look further?

---

