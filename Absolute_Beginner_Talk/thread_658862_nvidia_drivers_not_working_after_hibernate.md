---
title: "nvidia drivers not working after hibernate"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by darthshak on 2008-01-05
Hi everyone

      I installed Ubuntu 7.10(64 bit) on my flashy new Thinkpad T61. which came equipped with the nVidia Quadro NVS 140m 128 MB graphics card. Of course, initially, ubuntu was not able to configure the video card. So I downloaded the 169.07 drivers for my laptop. First problem was that setup complained something about OpenGL drivers not installing properly, but later on went on to say that setup was successful.

      I then decided to go to this link : [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61)
 as I was having issues with suspend and hibernate. After making the requisite changes, to acpi-support, suspend worked just fine. However, i changed "HIBERNATE_MODE" to "platform" and predictably, ubuntu shut down the computer on hibernate. However, when I booted my computer back on, I was greeted with a black screen saying that Ubuntu could not install drivers for my graphics card and forced me to use low graphics mode (I am using low graphics mode as i type this post). I decided to install the nvidia drivers again, and it uninstalled the previous drivers and installed again (once again, that vague error with opengl 32 bit). Once again, everything worked fine. Then, once again, when I shut down my laptop yesterday and switched it on now, i was greeted by the same low-graphics option....

Here is my acpi-support file : 

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=s3_mode

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="nvidia"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

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
HIBERNATE_MODE=platform

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
STOP_SERVICES="netapplet"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12   

Any ideas, coz I cant keep reinstalling nvidia drivers every time i restart ubuntu.

---

### Post by juaka on 2008-01-14
Try this  [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

