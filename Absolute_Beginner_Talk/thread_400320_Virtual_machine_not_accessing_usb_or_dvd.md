---
title: "Virtual machine not accessing usb or dvd"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by pollywog on 2007-04-03
Hello, I'm trying to go through a dry run on the feisty upgrade with my VMware player, but I can't seem to access either my usb hard drive, or a my dvd drive, to move the 1.8G backup  file into the virtual edgy set up in order to replicate my system. I love VMware player, but my inability to access large files is really limiting the usefulness of this program for me. I imagine that the problem is in the set up of my  .vmx file :

#!/usr/bin/vmplayer

# Filename: ubuntu_test.vmx
# Generated 2007-03-08;07:22:28 by EasyVMX!
# [http://www.easyvmx.com](http://www.easyvmx.com)

# This is a Workstation 5 or 5.5 config file
# It can be used with Player
config.version = "8"
virtualHW.version = "4"

# Selected operating system for your virtual machine
guestOS = "ubuntu"

# displayName is your own name for the virtual machine
displayName = "ubuntu_test"

# These fields are free text description fields
annotation = "ubuntu test"
guestinfo.vmware.product.long = "ubuntu test"
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
usb.generic.skipSetConfig = "TRUE"
usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"

# First serial port, physical COM1 is available
serial0.present = "TRUE"
serial0.fileName = "Auto Detect"
serial0.autodetect = "TRUE"
serial0.hardwareFlowControl = "TRUE"

# Optional second serial port, physical COM2 is not available
serial1.present = "FALSE"

# First parallell port, physical LPT1 is not available
parallel0.present = "FALSE"

# Sound settings
sound.present = "TRUE"
sound.virtualdev = "es1371"

# Logging
# This config activates logging, and keeps last log
logging = "TRUE"
log.fileName = "ubuntu_test.log"
log.append = "TRUE"
log.keepOld = "1"

# These settings decides interaction between your
# computer and the virtual machine
isolation.tools.hgfs.disable = "FALSE"
isolation.tools.dnd.disable = "FALSE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "e1000"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

# Settings for physical floppy drive
floppy0.present = "FALSE"

# Settings for physical CDROM drive
ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.startConnected = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.autodetect = "TRUE"

# First IDE disk, size 4800Mb
ide0:0.present = "TRUE"
ide0:0.fileName = "ubuntu_test.vmdk"
ide0:0.mode = "persistent"
ide0:0.startConnected = "TRUE"
ide0:0.writeThrough = "TRUE"

# END OF EasyVMX! CONFIG

ide0:0.redo = ""
ethernet0.generatedAddress = "00:0c:29:c2:68:af"
uuid.location = "56 4d 64 66 07 0a 2f 62-b3 70 fa 5d 50 c2 68 af"
uuid.bios = "56 4d 64 66 07 0a 2f 62-b3 70 fa 5d 50 c2 68 af"
checkpoint.vmState = "ubuntu_test.vmss"

I've got both a cd burner-master, and a dvd burner-slave. My ubuntu VM can access the cd, but not the dvd. My windowsXP VM is able to access both with similar settings. If anyone out there either sees the problem in the set up, or has a similar VM that is mounting the dvd and usb drives and would not mind posting the contents of their .vmx file I would greatly appreciate it! Thanks-P.W.

---

### Post by happymellon on 2007-04-10
The cd probalem come from the last  two sections:

# Settings for physical CDROM drive
ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.startConnected = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.autodetect = "TRUE"

# First IDE disk, size 4800Mb
ide0:0.present = "TRUE"
ide0:0.fileName = "ubuntu_test.vmdk"
ide0:0.mode = "persistent"
ide0:0.startConnected = "

If you look you have access to a hard disk and a single CD drive. You'd have to add a second CD drive entry. Add something like:

# Settings for physical CDROM drive
ide1:1.present = "TRUE"
ide1:1.deviceType = "cdrom-raw"
ide1:1.startConnected = "TRUE"
ide1:1.fileName = "auto detect"
ide1:1.autodetect = "TRUE"

after the section about the frist cd drive. If you look I changed the ide1:0 to ide1:1 to imply that you also wanted to add the second drive on the second IDE channel. Hope that helps

---

