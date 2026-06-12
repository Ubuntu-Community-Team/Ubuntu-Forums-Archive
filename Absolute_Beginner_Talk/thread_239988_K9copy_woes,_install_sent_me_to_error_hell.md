---
title: "K9copy woes, install sent me to error hell"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-08-20
Just tried installing k9copy, latest stable version via the instructions on the wiki.
Copied and pasted all code, but something seems to have gone extremely badly with the install.
eg.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
(cputest.cpp) available multimedia extensions: sse2
k9copy: /dev/hdc resolved to /dev/hdc
k9copy: /dev/hdc is block device (0)
k9copy: /dev/hdc seems to be cdrom
k9copy: (K3bDevice::Device) /dev/hdc: init()
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Mastering
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Track At Once
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD Read
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+RW
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R Double Layer
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD-R/-RW Write
k9copy: (K3bDevice::Device) /dev/hdc feature: Rigid Restricted Overwrite
k9copy: (K3bDevice::Device) /dev/hdc: dataLen: 60
k9copy: (K3bDevice::Device) /dev/hdc: checking for TAO
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO

and much, much more!

also if i now try updating my system, i get the following error.

E: /var/cache/apt/archives/libk9copy0_1.0.3.2-1_i386.deb: trying to overwrite `/usr/lib/libk9copy.la', which is also in package k9copy

Any ideas? 
all a bit too much for a ubuntu newcomer

---

### Post by rowanparker on 2006-08-20
You can install it using apt.
```
sudo apt-get install k9copy
```

Rowan.

---

### Post by stoer on 2006-08-20
yep, tried that...

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  k9copy: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installable
E: Broken packages
steve@laptop:~$

---

### Post by stoer on 2006-08-21
Hmm.
no experts as far as this app goes?
ok.

Shame that there's nothing stable/reliable in linux as far as ripping,decryptingand burning.  
Wine+decrypter/shrink is a working option but obviously defeats the point somewhat. 
Gnomebakker needs an iso to work from (pain if you already have the the dvd in vob (etc) format, seems so unecessary to convert it again just to burn it.
I've read that Nero has a linux version (19 dollars), that it works but is really a "poor cousin" in comparrison to it's windows version.
I'll keep trying, maybe i need to install KDE in order to run these apps (i keep reading that they are usable with Gnome, but.....)

Not sure if i've damaged my ubuntu sys with this attempt, everything seems ok  and i uninstalled k9copy using synaptic, the update error that i was getting resolved itself with the uninstall - naturally.

Anyways, onwards and fortitude.
Cheers.;)

---

### Post by rowanparker on 2006-08-21
It installed fine on my system, odd.

I will have a look into it.

Rowan.

---

### Post by Kilz on 2006-08-21
> **stoer said:**
> yep, tried that...

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  k9copy: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installable
E: Broken packages
steve@laptop:~$

To me it looks like you are trying to install the 1.0.4 version of k9copy. The easiest way to do it I have foud is to add [a german repository]("http://www.kubuntu.de/index.php?option=com_content&task=view&id=48&Itemid=70") to synaptic. Then use it to install the 1.0.4 version.
The only problem is the page is in german, but the repository address is in a grey box. Just open System > Adminastration > Synaptic. Click Settings > Repositories > +add > custom. Then paste in the addresses. Then reload synaptic. Do a search for k9copy. 
The repository also has the newest k3b. :D

---

### Post by stoer on 2006-08-21
Thanks for the tip.
Ok the german site was easy, address added as sugested.
Installed via synaptic - 

no k9copy in applications...with the terminal "k9copy"
and the following...

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
(cputest.cpp) available multimedia extensions: sse2
k9copy: /dev/hdc resolved to /dev/hdc
k9copy: /dev/hdc is block device (0)
k9copy: /dev/hdc seems to be cdrom
k9copy: (K3bDevice::Device) /dev/hdc: init()
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Mastering
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Track At Once
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD Read
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+RW
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R Double Layer
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD-R/-RW Write
k9copy: (K3bDevice::Device) /dev/hdc feature: Rigid Restricted Overwrite
k9copy: (K3bDevice::Device) /dev/hdc: dataLen: 60
k9copy: (K3bDevice::Device) /dev/hdc: checking for TAO
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO_R96P
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO_R96R
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R16
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    MODE SELECT (55)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        26
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R96P
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    MODE SELECT (55)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        26
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R96R
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    READ DVD STRUCTURE (ad)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        3a
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: READ DVD STRUCTURE length det failed
k9copy: (K3bDevice::Device) /dev/hdc:  Number of supported write speeds via 2A: 4
k9copy: (K3bDevice::Device) /dev/hdc : 4234 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 2822 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 1411 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 706 KB/s
k9copy: (K3bDevice::DeviceManager) setting current write speed of device /dev/hdc to 4234
k9copy: (K3bDevice::DeviceManager) Link: /dev/dvdrw -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/dvd -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/cdrw -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/cdrom -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/disk/by-path/pci-0000:00:1f.1-ide-1:0 -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/disk/by-id/ata-TSSTcorpCDDVDW_TS-L532A_Z44C503981 -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) SCANNING FOR GENERIC DEVICES.
k9copy: Could not resolve /dev/sg0
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg0for reading
k9copy: could not open device /dev/sg0 (No such file or directory)
k9copy: Could not resolve /dev/sg1
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg1for reading
k9copy: could not open device /dev/sg1 (No such file or directory)
k9copy: Could not resolve /dev/sg2
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg2for reading
k9copy: could not open device /dev/sg2 (No such file or directory)
k9copy: Could not resolve /dev/sg3
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg3for reading
k9copy: could not open device /dev/sg3 (No such file or directory)
k9copy: Could not resolve /dev/sg4
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg4for reading
k9copy: could not open device /dev/sg4 (No such file or directory)
k9copy: Could not resolve /dev/sg5
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg5for reading
k9copy: could not open device /dev/sg5 (No such file or directory)
k9copy: Could not resolve /dev/sg6
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg6for reading
k9copy: could not open device /dev/sg6 (No such file or directory)
k9copy: Could not resolve /dev/sg7
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg7for reading
k9copy: could not open device /dev/sg7 (No such file or directory)
k9copy: Could not resolve /dev/sg8
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg8for reading
k9copy: could not open device /dev/sg8 (No such file or directory)
k9copy: Could not resolve /dev/sg9
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg9for reading
k9copy: could not open device /dev/sg9 (No such file or directory)
k9copy: Could not resolve /dev/sg10
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg10for reading
k9copy: could not open device /dev/sg10 (No such file or directory)
k9copy: Could not resolve /dev/sg11
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg11for reading
k9copy: could not open device /dev/sg11 (No such file or directory)
k9copy: Could not resolve /dev/sg12
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg12for reading
k9copy: could not open device /dev/sg12 (No such file or directory)
k9copy: Could not resolve /dev/sg13
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg13for reading
k9copy: could not open device /dev/sg13 (No such file or directory)
k9copy: Could not resolve /dev/sg14
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg14for reading
k9copy: could not open device /dev/sg14 (No such file or directory)
k9copy: Could not resolve /dev/sg15
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg15for reading
k9copy: could not open device /dev/sg15 (No such file or directory)
k9copy: (K3bDevice::DeviceManager) scanning fstab: proc
k9copy: Could not resolve proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: Could not resolve proc
k9copy: proc resolved to proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: /dev/hda3 resolved to /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: /dev/hda1 resolved to /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: /dev/hda6 resolved to /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: /dev/hda5 resolved to /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: /dev/hda7 resolved to /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hdc
k9copy: (K3bDevice::DeviceManager) found device for /dev/hdc: /dev/hdc
k9copy: (K3bDevice::DeviceManager) scanning fstab: proc
k9copy: Could not resolve proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: Could not resolve proc
k9copy: proc resolved to proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: /dev/hda3 resolved to /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: /dev/hda1 resolved to /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: /dev/hda6 resolved to /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: /dev/hda5 resolved to /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: /dev/hda7 resolved to /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hdc
k9copy: (K3bDevice::DeviceManager) found device for /dev/hdc: /dev/hdc
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    READ DVD STRUCTURE (ad)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        3a
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: READ DVD STRUCTURE length det failed
k9copy: (K3bDevice::Device) /dev/hdc:  Number of supported write speeds via 2A: 4
k9copy: (K3bDevice::Device) /dev/hdc : 4234 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 2822 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 1411 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 706 KB/s
k9copy: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!
k9copy: /dev/hdc resolved to /dev/hdc
k9copy: /dev/hdc is block device (0)
k9copy: /dev/hdc seems to be cdrom
k9copy: (K3bDevice::Device) /dev/hdc: init()
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Mastering
k9copy: (K3bDevice::Device) /dev/hdc feature: CD Track At Once
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD Read
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+RW
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD+R Double Layer
k9copy: (K3bDevice::Device) /dev/hdc feature: DVD-R/-RW Write
k9copy: (K3bDevice::Device) /dev/hdc feature: Rigid Restricted Overwrite
k9copy: (K3bDevice::Device) /dev/hdc: dataLen: 60
k9copy: (K3bDevice::Device) /dev/hdc: checking for TAO
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO_R96P
k9copy: (K3bDevice::Device) /dev/hdc: checking for SAO_R96R
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R16
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    MODE SELECT (55)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        26
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R96P
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    MODE SELECT (55)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        26
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: checking for RAW_R96R
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    READ DVD STRUCTURE (ad)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        3a
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: READ DVD STRUCTURE length det failed
k9copy: (K3bDevice::Device) /dev/hdc:  Number of supported write speeds via 2A: 4
k9copy: (K3bDevice::Device) /dev/hdc : 4234 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 2822 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 1411 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 706 KB/s
k9copy: (K3bDevice::DeviceManager) setting current write speed of device /dev/hdc to 4234
k9copy: (K3bDevice::DeviceManager) Link: /dev/dvdrw -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/dvd -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/cdrw -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/cdrom -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/disk/by-path/pci-0000:00:1f.1-ide-1:0 -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) Link: /dev/disk/by-id/ata-TSSTcorpCDDVDW_TS-L532A_Z44C503981 -> /dev/hdc
k9copy: (K3bDevice::DeviceManager) SCANNING FOR GENERIC DEVICES.
k9copy: Could not resolve /dev/sg0
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg0for reading
k9copy: could not open device /dev/sg0 (No such file or directory)
k9copy: Could not resolve /dev/sg1
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg1for reading
k9copy: could not open device /dev/sg1 (No such file or directory)
k9copy: Could not resolve /dev/sg2
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg2for reading
k9copy: could not open device /dev/sg2 (No such file or directory)
k9copy: Could not resolve /dev/sg3
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg3for reading
k9copy: could not open device /dev/sg3 (No such file or directory)
k9copy: Could not resolve /dev/sg4
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg4for reading
k9copy: could not open device /dev/sg4 (No such file or directory)
k9copy: Could not resolve /dev/sg5
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg5for reading
k9copy: could not open device /dev/sg5 (No such file or directory)
k9copy: Could not resolve /dev/sg6
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg6for reading
k9copy: could not open device /dev/sg6 (No such file or directory)
k9copy: Could not resolve /dev/sg7
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg7for reading
k9copy: could not open device /dev/sg7 (No such file or directory)
k9copy: Could not resolve /dev/sg8
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg8for reading
k9copy: could not open device /dev/sg8 (No such file or directory)
k9copy: Could not resolve /dev/sg9
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg9for reading
k9copy: could not open device /dev/sg9 (No such file or directory)
k9copy: Could not resolve /dev/sg10
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg10for reading
k9copy: could not open device /dev/sg10 (No such file or directory)
k9copy: Could not resolve /dev/sg11
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg11for reading
k9copy: could not open device /dev/sg11 (No such file or directory)
k9copy: Could not resolve /dev/sg12
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg12for reading
k9copy: could not open device /dev/sg12 (No such file or directory)
k9copy: Could not resolve /dev/sg13
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg13for reading
k9copy: could not open device /dev/sg13 (No such file or directory)
k9copy: Could not resolve /dev/sg14
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg14for reading
k9copy: could not open device /dev/sg14 (No such file or directory)
k9copy: Could not resolve /dev/sg15
k9copy: (K3bDevice::Device) Error: could not open device /dev/sg15for reading
k9copy: could not open device /dev/sg15 (No such file or directory)
k9copy: (K3bDevice::DeviceManager) scanning fstab: proc
k9copy: Could not resolve proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: Could not resolve proc
k9copy: proc resolved to proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: /dev/hda3 resolved to /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: /dev/hda1 resolved to /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: /dev/hda6 resolved to /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: /dev/hda5 resolved to /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: /dev/hda7 resolved to /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hdc
k9copy: (K3bDevice::DeviceManager) found device for /dev/hdc: /dev/hdc
k9copy: (K3bDevice::DeviceManager) scanning fstab: proc
k9copy: Could not resolve proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: Could not resolve proc
k9copy: proc resolved to proc
k9copy: (K3bDevice::Device) Error: could not open device procfor reading
k9copy: could not open device proc (No such file or directory)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: /dev/hda3 resolved to /dev/hda3
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda3for reading
k9copy: could not open device /dev/hda3 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: /dev/hda1 resolved to /dev/hda1
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda1for reading
k9copy: could not open device /dev/hda1 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: /dev/hda6 resolved to /dev/hda6
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda6for reading
k9copy: could not open device /dev/hda6 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: /dev/hda5 resolved to /dev/hda5
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda5for reading
k9copy: could not open device /dev/hda5 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: /dev/hda7 resolved to /dev/hda7
k9copy: (K3bDevice::Device) Error: could not open device /dev/hda7for reading
k9copy: could not open device /dev/hda7 (Permission denied)
k9copy: (K3bDevice::DeviceManager) scanning fstab: /dev/hdc
k9copy: (K3bDevice::DeviceManager) found device for /dev/hdc: /dev/hdc
k9copy: (K3bDevice::ScsiCommand) failed: 
k9copy:                            command:    READ DVD STRUCTURE (ad)
k9copy:                            errorcode:  38
k9copy:                            sense key:  NO SENSE (2)
k9copy:                            asc:        3a
k9copy:                            ascq:       0
k9copy: (K3bDevice::Device) /dev/hdc: READ DVD STRUCTURE length det failed
k9copy: (K3bDevice::Device) /dev/hdc:  Number of supported write speeds via 2A: 4
k9copy: (K3bDevice::Device) /dev/hdc : 4234 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 2822 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 1411 KB/s
k9copy: (K3bDevice::Device) /dev/hdc : 706 KB/s
QObject::connect: No such signal k9Main::signalChangeStatusbar(const QString&)
QObject::connect:  (sender name:   'MainDlg')
QObject::connect:  (receiver name: 'k9Copy')
QObject::connect: No such signal k9Main::signalChangeCaption(const QString&)
QObject::connect:  (sender name:   'MainDlg')
QObject::connect:  (receiver name: 'k9Copy')


Then k9copy opens!
Any ideas?

K3B installed, sweet as a nut.

---

### Post by Kilz on 2006-08-21
> **stoer said:**
> Thanks for the tip.
Ok the german site was easy, address added as sugested.
Installed via synaptic - 

no k9copy in applications...with the terminal "k9copy"
and the following...


Then k9copy opens!
Any ideas?

K3B installed, sweet as a nut.


That happens every time I open it in a terminal. But the program works. I think its just looking for resources, or possibly its because we are using a KDE application on Gnome. I used the Alacarte menu editor to make a menu entry so I dont see it.

---

### Post by stoer on 2006-08-22
Ok!

Looked like a waterfall of fatal errors (in windows this would have been the build up to a "blue screen of death incident" :)  )

K9copy does seem to be working, need to make some space to try it out however, my 16gb partition seems to be diasappearing before my eyes - but that's another issue!

Made a link in the menu editor (as you suggested) - nice one, no more obvious waterfalls (at least it's now occuring only in the "unseen" background).
many thanks for your advice.

---

### Post by stoer on 2006-08-22
Woops.
got the following whilest trying to copy a previously ripped dvd.

An error occured while running DVDAuthor.
dvdauthor: dvdpgc.c218: genpgc:Assertion
'cd-(buf+d)<=128*8' failed.

This occured whilest logged in as 'user'
need to try as Root next.

---

### Post by stoer on 2006-08-24
I've the feeling that the last error message was more due to the DVD than to K9copy (i could be wrong  of cours).
The iso was from a ripped film that had some issues.  Under windows and with a couple of different programs i experienced some problems aswell.
Tried again today and completely successfully ripped a DVD.
So, i think only time will tell.
Thanks to everyone that had the time to advise me, much appreciated.

---

