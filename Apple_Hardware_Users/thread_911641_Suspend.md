---
title: "Suspend"
date: 2008-09-05
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-09-05
I can't get this machine to suspend...

Macbook Pro 3rd gen, ath9k, nvidia driver, Hardy.

Here is my acpi-support file ```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="sky2 ath_pci ath9k applesmc ndiswrapper"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

```

When I close the lid the apple blinks off then turns right back on. When I open it I just see a blinking "_". 
To get back to the desktop I have to switch to a Virtual terminal and then back to ctrl+alt+f7.

---

### Post by cyberdork33 on 2008-09-05
try messing with video related options. the double switch console one is necessary sometimes as well.

---

### Post by hanzomon4 on 2008-09-06
I've messed with every option I could think of, still not working.... not even close.

---

### Post by Qloor on 2008-09-07
As far as I know, suspending and resuming is impossible on a 3rd Gen. MacBook Pro. I've heard people say that they've gotten it to suspend but not resume, however I still don't believe either can currently be done. If you find a way to do it, please let us know.

---

