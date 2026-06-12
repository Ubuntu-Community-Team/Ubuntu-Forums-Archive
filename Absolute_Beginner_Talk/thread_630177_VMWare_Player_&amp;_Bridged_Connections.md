---
title: "VMWare Player &amp; Bridged Connections"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2007-12-03
I'm trying to install Ubuntu server edition on vmware player. The host machine is Gusty Desktop edition.

I'm trying to use a bridged connection, but IP addresses won't resolve to anything but 0.0.0.0. If I use a NAT connection, it connects just fine.

Essentially, I have no internet on the guest and no idea why. Both Ubuntu Server and CentOS are experiencing this problem, so I figure it's something about my vmware player setup.

Any ideas? Here's my vmx file:

```

#!/usr/bin/vmplayer

# Filename: Ubuntu_Gutsy_Server.vmx
# Generated 2007-12-02;07:41:08 by EasyVMX! 2.0 (beta)
# http://www.easyvmx.com

# This is a Workstation 6 config file
# It can be used with Player
config.version = "8"
virtualHW.version = "6"

# Selected operating system for your virtual machine
guestOS = "ubuntu"

# displayName is your own name for the virtual machine
displayName = "Ubuntu_Gutsy_Server"

# These fields are free text description fields
annotation = "Ubuntu Gutsy Server"
guestinfo.vmware.product.url = "http://www.beginnersunite.com/"
guestinfo.vmware.product.class = "virtual machine"

# Number of virtual CPUs. Your virtual machine will not
# work if this number is higher than the number of your physical CPUs
numvcpus = "1"

# Memory size and other memory settings
memsize = "512"
MemAllowAutoScaleDown = "FALSE"
MemTrimRate = "-1"

# PowerOn/Off options
gui.powerOnAtStartup = "TRUE"
gui.fullScreenAtPowerOn = "FALSE"
gui.exitAtPowerOff = "TRUE"

# Unique ID for the virtual machine will be created
uuid.action = "create"

# Settings for VMware Tools
tools.remindInstall = "TRUE"
tools.upgrade.policy = "upgradeAtPowerCycle"

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

# First serial port, physical COM1 is not available
serial0.present = "FALSE"

# Optional second serial port, physical COM2 is not available
serial1.present = "FALSE"

# First parallell port, physical LPT1 is not available
parallel0.present = "FALSE"

# Sound settings
sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"

# Logging
# This config activates logging, and keeps last log
logging = "TRUE"
log.fileName = "Ubuntu_Gutsy_Server.log"
log.append = "TRUE"
log.keepOld = "3"

# These settings decides interaction between your
# computer and the virtual machine
isolation.tools.hgfs.disable = "TRUE"
isolation.tools.dnd.disable = "FALSE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"

# Other default settings
svga.autodetect = "TRUE"
mks.keyboardFilter = "allow"
snapshot.action = "autoCommit"

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "e1000"
ethernet0.connectionType = "bridged"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"
ethernet0.wakeOnPcktRcv = "TRUE"

# Second network interface card
ethernet1.present = "FALSE"
ethernet1.virtualDev = "vmxnet"
ethernet1.connectionType = "nat"
ethernet1.addressType = "generated"
ethernet1.generatedAddressOffset = "10"
ethernet1.wakeOnPcktRcv = "TRUE"

# VNC - Remote Display
RemoteDisplay.vnc.enabled = "TRUE"
RemoteDisplay.vnc.port = "5900"

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
ide1:1.fileName = "/media/sda9/CD Images/ubuntu-7.10-desktop-i386.iso"
ide1:1.deviceType = "cdrom-image"
ide1:1.mode = "persistent"
ide1:1.startConnected = "TRUE"

# First IDE disk, size 30Gb
ide0:0.present = "TRUE"
ide0:0.fileName = "Ubuntu_Gutsy_Server.vmdk"
ide0:0.mode = "persistent"
ide0:0.startConnected = "TRUE"
ide0:0.writeThrough = "TRUE"

# EasyVMX! Shared Folder
sharedFolder.option = "alwaysEnabled"
sharedFolder0.present = "TRUE"
sharedFolder0.enabled = "TRUE"
sharedFolder0.readAccess = "TRUE"
sharedFolder0.writeAccess = "TRUE"
sharedFolder0.hostPath = "~/easyvmxfolder"
sharedFolder0.guestName = "EasyVMX! Shared Folder"
sharedFolder0.expiration = "never"
sharedFolder.maxNum = "1"

# END OF EasyVMX! CONFIG

extendedConfigFile = "Ubuntu_Gutsy_Server.vmxf"
virtualHW.productCompatibility = "hosted"

ethernet0.generatedAddress = "00:0c:29:26:21:37"
ethernet1.generatedAddress = "00:0c:29:e7:9f:2a"
uuid.location = "56 4d 57 e9 59 d2 19 41-ff d9 2b 8b ad 26 21 37"
uuid.bios = "56 4d 57 e9 59 d2 19 41-ff d9 2b 8b ad 26 21 37"
ide0:0.redo = ""
ethernet0.pciSlotNumber = "16"
ethernet1.pciSlotNumber = "-1"
sound.pciSlotNumber = "18"

checkpoint.vmState = ""

```

---

### Post by blop on 2007-12-03
What NIC is VM on VM player set to?

If you have a wireless and a LAN...it could be looking for a wireless IP when in fact you have a cable plugged into your LAN. Happened to me.

---

### Post by pteri498 on 2007-12-03
> **blop said:**
> What NIC is VM on VM player set to?
Where could I find this? Sorry for sounding ignorant, I've just never had to know this before.

> **blop said:**
> If you have a wireless and a LAN...it could be looking for a wireless IP when in fact you have a cable plugged into your LAN. Happened to me.
The host system's on wireless (nobody here wants another 50 foot cable spidering about the house). Could this be my issue? How could I fix this?

Thanks!

---

### Post by blop on 2007-12-03
Hi,

Im pretty certain now you have told me the host is on wireless that the issue is that the Virtual Machine is looking for IP on the LAN card.

Generally nic0 is LAN nic1 is Wireless....and VMs tend to default to the first NIC so....its looking for LAN...im 99% certain thats the problem

Now i dont use VM Player i use Workstation and ESX.... look in the settings...where you can select cdrom iso and usb things....there will be a network setting there.

---

### Post by pteri498 on 2007-12-03
> **blop said:**
> Hi,

Im pretty certain now you have told me the host is on wireless that the issue is that the Virtual Machine is looking for IP on the LAN card.

Generally nic0 is LAN nic1 is Wireless....and VMs tend to default to the first NIC so....its looking for LAN...im 99% certain thats the problem

Now i dont use VM Player i use Workstation and ESX.... look in the settings...where you can select cdrom iso and usb things....there will be a network setting there.

All right, I get what you're saying.

My wireleless card is actually listed right now as "ath0" (as opposed to "eth0"). Any tips on getting vmware player to reconcile itself with this card in bridged mode?

---

### Post by blop on 2007-12-03
HI, i just got home and have just had a look at VM player (apparantley it comes free with VM workstation) and errr no go im afraid the option to change the VM config is not there....

So you could try the other free product VM server that might do it...it has some more feature otherwise you need VM workstation.

and oddly enough there is a free trial...so you could edit the VM and then use it in Player!

[http://www.vmware.com/download/ws/eval.html](http://www.vmware.com/download/ws/eval.html)

good luck :)

---

### Post by pteri498 on 2007-12-03
Come to think of it, what if I tried to switch my wireless card to eth0 and my lan card to something else?

I've searched the forums, but I'm at a loss of how to do it. Not many results for changing network aliases, I guess.

Anyway, what do you guys think? What's the easiest way?

---

### Post by blop on 2007-12-04
Im a bit of a linux noob but an experienced windows IT techie...id say if your laptop works and your VM doesnt....fix the VM not the laptop.

Get the trial of workstation...and edit the VM

---

