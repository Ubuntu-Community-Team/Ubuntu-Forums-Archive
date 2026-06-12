---
title: "MacBook Pro 1,1: bad battery performance"
date: 2011-03-16
forum: Apple Hardware Users
---

### Post by demibatard on 2011-03-16
Hello,

I recently got my first gen macbook pro back up and running after installing a new hard drive and a new battery with Linux Mint (Ubuntu based, so I thought I would try here).

Everything works great, except the battery charge (after calibrating the battery) is stunningly short. After using the powertop utility, I found that the average power consumption is 28W! This is much too high...

So, I tried following this tutorial and installing the script mentioned here:

[http://mac.linux.be/content/improve-battery-life-macbook-ubuntu](http://mac.linux.be/content/improve-battery-life-macbook-ubuntu)

Unfortunately, it didn't work. I am still getting high power consumption. I tried turning off the bluetooth device and setting the monitor brightness to a low setting, but this didn't make much of a difference. :confused:

Any ideas on how to improve the battery performance would be very welcome!! :)

Thanks.

---

### Post by wweeks on 2011-03-16
I would recommend changing your settings so the disks will spin down when possible.

---

### Post by Joe of loath on 2011-03-16
Install powetop, and see if the processors are scaling back when unused.

---

### Post by demibatard on 2011-03-16
I managed to improve performance slightly by installing laptop-mode-tools, but Linux is still consuming too much power. 

This is the output after executing powertop -d in terminal:

```

PowerTOP 1.13   (C) 2007 - 2010 Intel Corporation 

Collecting data for 15 seconds 


Your CPU supports the following C-states : C1 C2 C3 C4 
Your BIOS reports the following C-states : C1 C2 C4 
Cn	          Avg residency
C0 (cpu running)        ( 0.0%)
polling		  0.0ms ( 0.0%)
C1 mwait	  0.0ms ( 0.0%)
C2 mwait	  0.5ms ( 2.4%)
C4 mwait	  0.9ms (97.9%)
P-states (frequencies)
  2.17 Ghz     4.7%
  2.00 Ghz     0.0%
  1.84 Ghz     0.0%
  1500 Mhz     0.1%
  1000 Mhz    95.2%
Disk accesses:
Wakeups-from-idle per second : 1106.2	interval: 15.0s
Power usage (ACPI estimate): 24.6W (0.3 hours) 
No detailed statistics available; please enable the CONFIG_TIMER_STATS kernel option
This option is located in the Kernel Debugging section of menuconfig
(which is CONFIG_DEBUG_KERNEL=y in the config file)
Note: this is only available in 2.6.21 and later kernels

An audio device is active 100.0% of the time:
hwC0D0 SigmaTel STAC9221 A1 

A USB device is active 100.0% of the time:
USB device  2-2 : Apple Internal Keyboard / Trackpad (Apple Computer)

Suggestion: Enable wireless power saving mode by executing the following command:
  iwconfig wlan0 power timeout 500ms
This will sacrifice network performance slightly to save power.

Recent USB suspend statistics
Active  Device name
  0.0%	/sys/bus/usb/devices/5-1
  0.0%	USB device  4-2 : IR Receiver (Apple Computer, Inc.)
100.0%	USB device  2-2 : Apple Internal Keyboard / Trackpad (Apple Computer)
  0.0%	/sys/bus/usb/devices/1-4
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.38-6-lowlatency uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.38-6-lowlatency uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.38-6-lowlatency uhci_hcd)
100.0%	USB device usb2 : UHCI Host Controller (Linux 2.6.38-6-lowlatency uhci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.38-6-lowlatency ehci_hcd)

Runtime Device Power Management statistics
Active  Device name
  0.0%	0c:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 
  0.0%	03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter 
  0.0%	02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller 
  0.0%	01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
  0.0%	00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller 
  0.0%	00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller 
  0.0%	00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller 
  0.0%	00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 
  0.0%	00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 
  0.0%	00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 
  0.0%	00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 
  0.0%	00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 
  0.0%	00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 
  0.0%	00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 
  0.0%	00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller 
  0.0%	00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port 

Devices without runtime PM
i2c:lm63






00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge 
00:07.0 Performance counters: Intel Corporation Device 27a3 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub 

Recent audio activity statistics
Active  Device name
100.0%	hwC0D0 SigmaTel STAC9221 A1 

Recent SATA AHCI link activity statistics
Active	Partial	Slumber	Device name

```

---

### Post by demibatard on 2011-03-19
I was able to slightly decrease power consumption by modifying the laptop-mode.conf and its associated configuration files, however I am still getting a minimum power usage of 23.5W according to powertop (this is when the laptop is doing practically nothing -- no applications other than window manager, Xorg, basic daemons like syndaemon, etc.).

Why is the power consumption so high? Are there any other tools available for decreasing battery consumption? For the record, I just bought this battery and can't even get two hours worth of use running the battery with normal laptop activity (surfing the web, writing email, doing my C++ assignments, etc.)

I would rather not switch back to OS X, but I may just do that if I can't get the power consumption under control... any help would be greatly appreciated!

Thanks. :)

---

### Post by bd1308 on 2011-03-20
Have you checked your CPU to see if it's always running at full speed. I had to install 'cpufrequtils' and when i did that, the CPU "ondemand" governor took over and my Powerbook is throttling very nicely. My battery life is oh so much better than before.

---

### Post by demibatard on 2011-03-20
Yes, I have cpufreqd and cpufrequtils installed. Both CPU governors are set to "ondemand". Additionally, I have laptop-mode-tools installed, which also has CPU scaling enabled, CPU governor set to "ondemand" there as well. Just to make sure, I checked the kernel config file and the CPU governor is enabled there too.

I am averaging about 23W when my laptop is idling (i.e. not surfing the web, checking email, writing a text document, or anything!)

---

