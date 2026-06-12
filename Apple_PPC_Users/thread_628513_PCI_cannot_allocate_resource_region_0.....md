---
title: "PCI: cannot allocate resource region 0...."
date: 2007-12-01
forum: Apple PPC Users
---

### Post by jmelton on 2007-12-01
When I boot up into Feisty in my iBook G4, I see the following error messages:
PCI: cannot allocate resource region 0 of device 0001:10:18.0
PCI: cannot allocate resource region 0 of device 0001:10:19.0

Bootup then proceeds without any hitches.  Does anyone have any idea what this means, what it would affect, or how to fix it if it's a problem?  I've googled it and searched around the forums, and haven't found much info.  It does seem to be a common bootup error message in PPC machines.

My wireless isn't working yet, as noted in another thread, but I'm not sure if this has anything to do with that.

---

### Post by Zaelore on 2007-12-01
I have an iBook g4 as well and I get the same errors on start up. Don't worry, it doesn't affect anything as far as I know. I don't think it has anything to do with getting your wireless working.

---

### Post by jmelton on 2007-12-01
> **Zaelore said:**
> I have an iBook g4 as well and I get the same errors on start up. Don't worry, it doesn't affect anything as far as I know. I don't think it has anything to do with getting your wireless working.

Thanks for the info.  Is your wireless working?  If so, what did you do to get it working, or did it just work straight out of the box?

---

### Post by foolsh on 2007-12-05
I see that same error on mine. I wonder if it has anything to do with the nvidia chip set.
I installed gusty on first boot the restricted drivers manager notified me there was a non-free driver for the wifi I clicked through that now it works.
Or 
sudo aptitude install bcm43xx-fwcutter

---

### Post by UKRTornado on 2007-12-05
I get a similar error trying to install Kubuntu Fesity on my G4 powerbook (a later model)...
I'm really not very good at this sort of stuff... here's what happens

Boots fine off the disk
Press enter to run the default installer
Gets up to "Checking RAMDisk" stage, then cuts to the apple grey backround
Then goes back to the White-on-black and gives me the error message about not being able to allocate resource region.
Shuts down

As I say, I'm really new at this sort of stuff - anyone got any tips?

Thanks in advance.

EDIT: Just tried it with an Ubuntu Feisty disk, burned off my PC rather than my laptop, got the same error, then saw a brief flash of the ubuntu logo before it shutdown again.

---

### Post by stmiller on 2007-12-05
This is a [common]("http://www.google.com/search?q=PCI%3A+cannot+allocate+resource+region+0") message, not specific to powerpc.  Type
```

lspci

```

or 

```

dmesg

```

into a terminal and look for device 0001:10:18.0 and 0001:10:19.0 from your error messages. Then you will know what hardware it is talking about. Probably it's the video, and it's okay as long as it continues to boot up normally.

---

### Post by UKRTornado on 2007-12-05
Unfortunately that doesn't help... I only get the one error - 0001:10:19.0.

Using lspci returns invalid command, using dmesg give me a lot of text with no mention of that PCI device:

```
standard timeslicing quantum is 10000 us
vm_page_bootstrap: 253544 free pages
mig_table_max_displ = 70
98 prelinked modules
Copyright (c) 1982, 1986, 1989, 1991, 1993
        The Regents of the University of California. All rights reserved.

using 2621 buffer headers and 2621 cluster IO buffer headers
IOPCCard info:   Intel PCIC probe:   TI 1510 rev 00
FireWire (OHCI) Apple ID 31 built-in now active, GUID 000d93ff fe6061f4; max speed s800.
CSRHIDTransitionDriver::probe: 
CSRHIDTransitionDriver::start before command
Security auditing service present
BSM auditing present
disabled
rooting via boot-uuid from /chosen: B53CA071-4027-3E27-A9A1-F3BA9A0B3876
Waiting on <dict ID="0"><key>IOProviderClass</key><string ID="1">IOResources</string><key>IOResourceMatch</key><string ID="2">boot-uuid-media</string></dict>
Got boot device = IOService:/MacRISC2PE/pci@f4000000/AppleMacRiscPCI/ata-6@D/AppleKauaiATA/ATADeviceNub@0/IOATABlockStorageDriver/IOATABlockStorageDevice/IOBlockStorageDriver/Hitachi HTS541080G9AT00 Media/IOApplePartitionScheme/Untitled@3
BSD root: disk0s3, major 14, minor 2
CSRHIDTransitionDriver::stop
IOBluetoothHCIController::start Idle Timer Stopped
Jettisoning kernel linker.
Resetting IOCatalogue.
Matching service count = 0
Matching service count = 1
Matching service count = 1
Matching service count = 1
Matching service count = 1
Matching service count = 1
IPv6 packet filtering initialized, default to accept, logging disabled
UniNEnet: Ethernet address 00:0d:93:60:61:f4
AirPortPCI_MM: Ethernet address 00:11:24:91:48:ed
Registering For 802.11 Events
[HCIController][setupHardware] AFH Is Supported
ATY,Jasper_A: vram [b8000000:04000000]
ATY,Jasper_B: vram [b8000000:04000000]
IOBluetoothBNEPDriver: Ethernet address 00:11:24:66:bf:80
AirPort:  Link Active:  "Bushwood" - 00173f4ae983 - chan 3
```

...doesn't mean much to me. And mine just will not install, so unfortunately it does matter!

Thanks again

---

### Post by rhetoric on 2007-12-05
I have the same messages during boot. I'm assuming it's related to the analog modem for which there are no linux drivers. If I'm wrong, or if I'm right and someone knows how to remove attempts to configure this device during boot (to speed up boot and get rid of the annoying messages), then by all means please post some info. Thanks.

---

### Post by stmiller on 2007-12-06
> **UKRTornado said:**
> Unfortunately that doesn't help... I only get the one error - 0001:10:19.0.

UKR: Sorry I should have been more specific. I was replying to the OP who mentioned he had those two addresses. Those numbers are the PCI hardware address of different devices, so everyone's machine is different.

Try doing this and scan for your boot error device to figure out what it is:

```

cat /var/log/messages |more

```

You are able to boot the machine it seems (?) so what problem are you having?

---

### Post by UKRTornado on 2007-12-06
> **stmiller said:**
> UKR: Sorry I should have been more specific. I was replying to the OP who mentioned he had those two addresses. Those numbers are the PCI hardware address of different devices, so everyone's machine is different.

Try doing this and scan for your boot error device to figure out what it is:

```

cat /var/log/messages |more

```

You are able to boot the machine it seems (?) so what problem are you having?

Hi mate, no worries - not sure if I should put my problem in a new thread, as it's a really a different problem I'm having caused by the same thing.
I can boot to OSX fine, but when I try and boot ubuntu live off the disk, I get this error about PCI device 0001:10:19.0 and it shuts down. I just realised what I said may have been a bit ambiguous... I meant to say running live off the disk rather than installing it (however I know I want to install it - is there an easier way of doing this?).
As I say sorry for anything I get wrong etc, I'm more or less a complete linux noob :D

EDIT: Tried cat /var/log/messages |more - I get a message saying "cat: /var/log/messages: No such file or directory"

Surely this scans for errors when booting into linux? Cause I don't get the error when booting into OSX, and as I say, I can't get into linux because of the error :(

---

### Post by foolsh on 2007-12-13
dont use the live installer use the alterate install disk instead I allways do make life easier for me.
[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

---

