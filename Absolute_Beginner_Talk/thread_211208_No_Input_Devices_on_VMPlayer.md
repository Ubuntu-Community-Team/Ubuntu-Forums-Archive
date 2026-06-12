---
title: "No Input Devices on VMPlayer"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Eltern on 2006-07-07
So I'm trying to install Windows XP on Kubuntu, using VMplayer and a virtual machine I created with [www.easyvmx.com](www.easyvmx.com). But when I run VMplayer, I lose my keyboard and mouse. This only happens when I ctrl+a to grab the VMplayer window, or click on it. Once I'm "in" the VMplayer I can't use my USB keyboard and mouse, or the keyboard and mouse built into my laptop.

The program still runs. If I have an XP CD in the drive it will start booting /installing it, but I can't hit enter to keep going. 

CD-ROM 2, the serial port, the parallel port, and the sound adapter all do not work on booting up the virtual machine. I assume it's a problem with the serial port or parallel port. 

This is my .vmx file:

#!/usr/bin/vmplayer

# Filename: My_Virtual_Machine.vmx
# Generated 2006-07-07;03:41:03 by EasyVMX!
# [http://www.easyvmx.com](http://www.easyvmx.com)

# This is a Workstation 5 or 5.5 config file
# It can be used with Player
config.version = "8"
virtualHW.version = "4"

# Selected operating system for your virtual machine
guestOS = "winxppro"

# displayName is your own name for the virtual machine
displayName = "My_Virtual_Machine"

# These fields are free text description fields
annotation = "Windows XP"
guestinfo.vmware.product.url = "http://www.easyvmx.com/"
guestinfo.vmware.product.class = "virtual machine"

# Number of virtual CPUs. Your virtual machine will not
# work if this number is higher than the number of your physical CPUs
numvcpus = "1"

# Memory size and other memory settings
memsize = "320"
MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

# Unique ID for the virtual machine will be created
uuid.action = "create"

# Remind to install VMware Tools
# This setting has no effect in VMware Player
tools.remindInstall = "TRUE"

# Startup hints interfers with automatic startup of a virtual machine
# This setting has no effect in VMware Player
hints.hideAll = "TRUE"

# Enable time synchronization between computer
# and virtual machine
tools.syncTime = "TRUE"

# USB settings
# This config activates USB
usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"

# First serial port, physical COM1 is available
serial0.present = "TRUE"
serial0.fileName = "COM1"
serial0.hardwareFlowControl = "TRUE"

# Optional second serial port, physical COM2 is not available
serial1.present = "FALSE"

# First parallell port, physical LPT1 is available
parallel0.present = "TRUE"
parallel0.fileName = "LPT1"
parallel0.bidirectional = "TRUE"

# Sound settings
sound.present = "TRUE"
sound.virtualdev = "es1371"

# Logging
# This config activates logging, and keeps last log
logging = "TRUE"
log.fileName = "My_Virtual_Machine.log"
log.append = "TRUE"
log.keepOld = "1"

# These settings decides interaction between your
# computer and the virtual machine
isolation.tools.hgfs.disable = "FALSE"
isolation.tools.dnd.disable = "TRUE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "vlance"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

# Second network interface card
ethernet1.present = "TRUE"
ethernet1.virtualDev = "vlance"
ethernet1.connectionType = "nat"
ethernet1.addressType = "generated"
ethernet1.generatedAddressOffset = "10"

# Settings for physical floppy drive
floppy0.present = "FALSE"

# Settings for physical CDROM drive
ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.startConnected = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.autodetect = "TRUE"

# Settings for the optional virtual CDROM, ISO-image
ide1:1.present = "TRUE"
ide1:1.fileName = ".iso"
ide1:1.deviceType = "cdrom-image"
ide1:1.mode = "persistent"
ide1:1.startConnected = "FALSE"

# First IDE disk, size 4Gb
ide0:0.present = "TRUE"
ide0:0.fileName = "My_Virtual_Machine.vmdk"
ide0:0.mode = "persistent"
ide0:0.startConnected = "TRUE"
ide0:0.writeThrough = "TRUE"

# END OF EasyVMX! CONFIG

ide0:0.redo = ""
ethernet0.generatedAddress = "00:0c:29:59:7e:49"
ethernet1.generatedAddress = "00:0c:29:59:7e:53"
uuid.location = "56 4d b1 a3 c5 e2 0d 11-6e 51 ef b5 d7 59 7e 49"
uuid.bios = "56 4d b1 a3 c5 e2 0d 11-6e 51 ef b5 d7 59 7e 49"
checkpoint.vmState = "My_Virtual_Machine.vmss"

Thanks!

---

### Post by bartbes on 2006-07-08
Maybe you should try the (absolutely) free VMWare Server. With which you can create Virtual Machines.. which are configured for your system

---

### Post by Eltern on 2006-07-08
I'd rather not, in principle, because theoretically this -ought- to "just work". However, I've scoured the net and I haven't found anyone who's had a similar problem, which is frustrating.

Also, I have read about and experienced problems with installing new VMWare products when you had other ones at one point, because they won't install if they find the smallest trace of another VMWare program. So, I'd rather just make this one work. Also, the VMWare server program seems to be far from troubles, judging by the number of posters having issues with it. EasyVMX + VMplayer has purportedly been comparatively easy. Guess not :D 

If it might matter at all, I'm using a Toshiba laptop.

Thanks for the help!

---

