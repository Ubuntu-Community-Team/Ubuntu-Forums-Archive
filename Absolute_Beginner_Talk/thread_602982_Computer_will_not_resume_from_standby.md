---
title: "Computer will not resume from standby"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by jollins on 2007-11-04
Hi

With compiz enabled, my computer will enter suspend fine, but when attempting to resume my screen will remain black, except for the character Ç followed by a few more random other characters appearing in the upper region of the screen. No cursor visible, and the keyboard does not seem to do anything. Suspend used to work fine but stopped recently for whatever reason. I've tried following the advice listed[URL="http://ubuntuforums.org/showthread.php?t=462089&highlight=suspend+to+ram"] _here_
[/URL], but no success so far.

Suspend works now only if I disable compiz but thats no fun.

Hardware/software
HP dv6500 w/ Intel gm965 (x3100)
Ubuntu Gutsy

Edit: Just to clarify, by "standby" I mean "suspend"

My /etc/default/acpi-support:

```
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
MODULES=""

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
STOP_SERVICES="networking"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12
```

Can anyone help?

---

### Post by chris.m.ball on 2007-11-04
I've had similar issues with both standby and hibernation.  I'm running a Sony Vaio A-Series, 2ghz Pentium M, 1GB Ram.  From everything I've read, many people have standby and hibernation completely working.  I think we may be cursed...:(

---

### Post by P4man on 2007-11-04
I got a feeling many more have problems with it, including me. 

On my desktop, nothing works, neither standby nor hibernate. On my "old'" laptop, standby works fine, hibernate doesnt. On my second laptop, hibernate works, standby works except the wifi fails one out of 3 times on resuming.

I often read Linux advocates blaming BIOS developers for not following standards and such, and while that may be true, on all these machines Windows does it just fine. End users don't care who is to blame, the perceive windows to work, and Linux to be buggy.

Anyway, you could try  uswsusp I guess:
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

I havent tried it under Gutsy yet, I did cure it on Feisty

---

### Post by jollins on 2007-11-05
Suspend actually works fine when compiz is disabled. Apparently this is a somewhat common problem but I can't seem to find a fix that is designed with intel GPUs in mind.

---

