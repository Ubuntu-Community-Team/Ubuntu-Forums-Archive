---
title: "Motherboard wakes from suspend immediately"
date: 2012-09-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by AshersM on 2012-09-27
Hi everyone!

I've installed Ubuntu 12.04.1 on my homebuilt ITX box and everything works great, except for suspend. If you suspend the machine, it will go into suspend mode, and wakes after 3 seconds. Viewing the logs doesn't seem to give a reason for the wake event. I've tried booting in both UEFI and CSM mode. Tried the xorg-edgers repository. I've even tried shutting off as many onboard devices as I can, that was no help. Any idea's?

Here's the specs:
Ubuntu 12.04.1 64bit
Asus P8Z77-I Deluxe (latest firmware 607)
Intel Core i5-3770K
Using Intel HD4000 graphics
Patriot Gamer 2 series 8GB (2x4GB) DDR3 1600Mhz
Kingston SV100S2/128G
Seagate Barracuda LP ST31500541AS
LG Slimline DVD drive

---

### Post by AshersM on 2012-09-28
I appear to have mixed the issue. There was some ACPI naughtiness that I hold overlooked. I tried disabling wake from USB and GLAN, no solution. Disabled wake by PWRB (Power Button) and everything is great! Strangely though, I can still wake using the power button!

Here's what I added to my rc.local

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
#
#Echo PWRB to the ACPI wakeup file to disable waking up with the power button
echo PWRB > /proc/acpi/wakeup
echo "rc.local has completed sucessfully." >> /tmp/resume.log
exit 0

```

---

### Post by milou on 2013-06-19
Hi, old post but same issue with Ubuntu 13.04 (64 bits) and same hardware (P8Z77-I/Interl HD4000) with latest BIOS. Will try this fix this evening!

---

