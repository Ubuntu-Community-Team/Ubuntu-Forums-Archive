---
title: "VHD cloned to USB - boots on PC, won't boot on Mac - pulling my hair out"
date: 2016-01-11
forum: Apple Hardware Users
---

### Post by Aaron_Casper on 2016-01-11
I have built a Virtual Machine using Ubuntu 15.10 as a guest under VirtualBox that is configured as a "kiosk" type machine.  Add the Oracle extensions pack, and it runs like a champ.

 The .VHD for this Virtual Machine can be cloned to a USB drive quite easily and will boot on almost any x86 hardware... EXCEPT for Mac.

 I've tested it against a wide variety of x86-based PCs with roaring success.  In fact, there are only a small list of machines that simply refuse to boot from this USB storage.  Even newer Win8/10 machines will accept it once you bypass SecureBoot.

 My testbed in the office for this is a mid-2012 MBP 13-inch with a 2.5ghz i5 and 16gb of RAM running OS-X 10.10.5

 I did manage to make one USB drive that will boot for Mac by building my kiosk "baremetal".  Put simply, I installed Ubuntu to the USB drive as if it were a SATA device on the Mac.

 Here's where things get WEIRD.  I then (mistakenly) repurposed that same USB drive for something else.  On a whim, I tried cloning my "PC-compatible" VHD back to it, and it boots on Mac still!  Something outside the scope of normal is going on here.

 I've even had this mysteriously working USB drive side-by-side against a non-working "clone" of it in a hex debugger and can't find this accidental "secret sauce".  diff returns that the two (as unmounted /dev/sdb and /dev/sdc under a development VM) are in fact different, but no differences are anywhere near the MBR.

 The "patient-zero" USB drive comes up in the bootloader upon using [Alt/Option] after the startup chime.  Any clones show in the menu as well, but upon selecting a drive that isn't this one special case, it presents "No bootable media - press any key"

 Now, a few catches to this problem...  I cannot use rEFIt or rEFInd, nor can I permanently modify the firmware/BIOS/whatever-Apple-calls-it on the target system.  These "kiosks" are built for our end users, and I fear for their Mac if we recommend any of that.  The goal is to have a plug-n-pray solution that removes the users personal configuration from the equation.  A locked-down linux-based kiosk that prevents their (sometimes questionable) configuration choices from interfering with work.


 What special Apple black-magic am I missing to make a USB drive that isn't from Apple happily boot on a Mac?  I'm completely puzzled as to why Apple seems to ignore grub2 unless it was installed baremetal.

---

