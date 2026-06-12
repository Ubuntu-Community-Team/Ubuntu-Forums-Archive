---
title: "32-bit Win API Environment for PPC"
date: 2006-10-20
forum: Apple PPC Users
---

### Post by jaradronald on 2006-10-20
Has anybody had any experience compilling WINE or another Windows Emulator for Linux on the PPC?  :confused:   I know it has to be possible, considering the myriad of commercial "Windows Emulators" that are available for OS X.

I know, I know, "Wine Is Not an Emulator" but I'm tired of hearing how it's impossible to compile a Windows 32-bit API for PPC without any good reason as to why...  I understand that the binary layers are different for the two processors, and this is one aspect of the ease of compilling Wine in a x86 environment, but there must be somebody out there with enough knowledge of the interworking of the Applications layers to port Wine in Linux for PPC.  I hear that VMWare has their x86 PPC emulation system in Beta...

---

### Post by shadie on 2006-10-20
I installed QEMU and Windows 2000 last week on a Powerbook G4 667Mhz, I followed the guide in the wiki for installing on Intel with XP which went without a hitch.

It runs fine, similar speed to VPC, not had a crash yet, here's a quick and dirty howto.

sudo apt-get install qemu vgabios

(Note: there is also a vgabios setup for saving screen resolution information that you have to go through)

qemu-img create -f qcow winxp.img 2G 

(Creates a hard drive image)

qemu -localtime -hda winxp.img -cdrom /dev/hdc -m 196 -boot d 

(Boots install CD, I used an external firewire DVDRW which worked fine)

qemu winxp.img -cdrom /dev/cdrom -soundhw all -net user -net nic -m 256 -localtime

(Boots W2K after installation is finished, note if you list -cdrom you must have a cd in the drive to start)

That's all I did to install W2K, network is good, screen resolution changes are fine.


Cheers,

---

