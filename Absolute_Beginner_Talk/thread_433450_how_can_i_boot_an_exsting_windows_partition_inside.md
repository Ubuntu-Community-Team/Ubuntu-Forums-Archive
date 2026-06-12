---
title: "how can i boot an exsting windows partition inside ubuntu?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-05-05
i have my computer set to dual boot ubuntu 6.10 and xp. I would like to boot my wondows partition virtually from inside ubuntu. is there a way to do this?

 A friend was telling me about virtual box but said that it had to make a copy of the xp partition to do it. is there any way to boot the existing partition and not have to make a copy of it?

---

### Post by crispy_420 on 2007-05-05
There are options for booting XP in windows within windows but I don't think what you want is an option. Just knowing XP and it's ability to be stickler for hardware, not sure if you can run your current install through emulation. Sorry!

---

### Post by schmidtbag on 2007-05-05
Theres something called win4lin that does exactly what you want but it's gonna be a clean start of windows.  You have to pay for it eventually ($40 I think) and I tried it before but didn't like it because none of my usb things were detected but if you get any luck with it lemme know i'd like to see how that turns out.   Just google it if you want it - its not very hard to find.

---

### Post by AnRa on 2007-05-05
Maybe you find this useful:
 :arrow: [Run Existing Windows installation With Vmware Player](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)
Good luck! ;)

---

### Post by seriousjohn on 2007-05-10
I have followed this guide and get a grub error 21. Has anybody else had that and how did you get around it?

widows.vmdk
```
# Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 117266624 FLAT "/dev/sda" 63 



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "ide"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "7299"
```

windows.vmx
```

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = "56 4d 75 cc b2 fc 3a 41-08 a4 a7 4d 37 eb 4e e1"
uuid.bios = "56 4d 75 cc b2 fc 3a 41-08 a4 a7 4d 37 eb 4e e1"

uuid.action = "create" 
checkpoint.vmState = "" 

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "512" 
paevm = "TRUE" 
sched.mem.pshare.enable = "TRUE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "TRUE" 
tools.remindinstall = "FALSE" 
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:eb:4e:e1"
ethernet0.generatedAddressOffset = "0"

usb.present = "FALSE" 
usb.generic.autoconnect = "FALSE" 

sound.present = "TRUE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "TRUE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 

floppy0.present = "FALSE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "FALSE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"
```


Thanks,
John

---

