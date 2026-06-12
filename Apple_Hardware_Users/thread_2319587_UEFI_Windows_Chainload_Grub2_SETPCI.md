---
title: "UEFI Windows Chainload Grub2 SETPCI"
date: 2016-04-05
forum: Apple Hardware Users
---

### Post by TGIK on 2016-04-05
Hello yall! 

I have a 2011 MBP with Ubuntu, OSX, FreeBSD, Windows 10 (All UEFI) --- 

The issue I have (which is well documented) is that because of a combination of Apple's EFI 1.1 implementation coupled with how windows 'sees' devices on boot the audio PCI bridge and all audio ports are not recognized under windows 10. Of course Linux and FreeBSD work out of the box (except on FreeBSD with the BCM4331) which is amazing but also really frustrating that Apple and Windows (with all the financial resources in the world) can't 'make it work' (though they might have all that money because of 'planned obsolescence' ) 

Apple will probably not update the firmware of their 2013 Macs to be UEFI 2.0 compliant (though they should) 
Microsoft will probably not change the way their bootloader probes devices UEFI (though they should) 

so in my head I have two options that may work or may just be fool hardy --

one is to mess with PCI registers in an UEFI shell -- there is some written about this in regards to macs and video cards (specifically the ones that have NVIDIA optimus) but I really have no basis on where to start from that angle --- and no one has messed with the cirrus/intel audio pci registers 


the other idea I had was to use set pci in the windows 10 efi grub 2 entry to point windows to right places to look--


the first question about that is -- does setpci work when you chainload or does it only work for linux kernels ?

my fantasy (and I am aware that that is what it might be) is that I can take all the PCI information from my working linux OS and pass those PCI definitions to windows boot manger via setpci commands in the grub entry. 


Is this possible?

---

### Post by gravysteak on 2016-12-01
Yes setpci will work for windows. You can test by pressing c to get command line in grub then entering your setpci command and then lspci to confirm changes were ok.

i then added to /etc/grub.d/30 osprober script my setpci command
```
#! /bin/sh
set -e
echo "setpci -d 8086:2682 90.b=40"
```

---

