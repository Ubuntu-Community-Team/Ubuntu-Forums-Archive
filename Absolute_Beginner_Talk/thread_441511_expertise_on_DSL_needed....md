---
title: "expertise on DSL needed..."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Jareth on 2007-05-12
howdy,
I'm trying to get Damn small Linux on a USB flash drive (just for giggles really).
I'm using windows 98 to do it cos it seemed the easier option, me not being confident on ubuntu terminals and all.
Here are the instructions I'm using:

"Note: This guide assumes that your USB Flash Drive is "I:". Please replace I with the correct drive letter.

    * Format your drive (FORMAT I: /fs:FAT32)
    * Download DSL (dsl-embedded.zip), [http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)
    * Copy DSL to your USB drive(Unzip DSL and copy all files)
    * Download Syslinux - Syslinux can also be used by various other platforms, such as Unix.
    * Go to a command prompt and run syslinux for your drive from \win32\syslinux.exe (SYSLINUX I:)
    * reboot. 

Note: Booting from USB may or may not work on your computer, mostly dependent on its age and bios setup. Some systems may have problems booting from USB drives formatted as FAT32. Changing the format step to FORMAT I: /fs:FAT may allow DSL to boot."

I'm up to the part with syslinux, and I get stuck cos its not clear enough for me to know what I should be doing? (Erm?)

"* Go to a command prompt and run syslinux for your drive from \win32\syslinux.exe (SYSLINUX I:)"

First. where should syslinux-3.36.zip be sitting for this command? Should I have it on the flash drive with the other files or just on my desktop somewhere?

Is it possible to skip this bit?


Appreciate any help, Ta!

---

### Post by Campingman on 2007-05-12
Is this a better guide?
[http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl](http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl)
 Pen drive linux are usually pretty good, i have not tried dsl but most of the other guides work
I have successfully installed Ubuntu, knoppix and pcoslinux on pen drive

---

### Post by FuturePast on 2007-05-12
It's not possible to skip that bit as syslinux makes the flash drive bootable.

First unzip syslinux-3.36.zip to your desktop.

Then run syslinux.exe i:

Make sure that "i:" is your flash drive first.

---

### Post by Jareth on 2007-05-12
Great stuff, now it is saying:

"You need to be running at least Windows NT; use syslinux.com instead."

bit more help please

---

### Post by FuturePast on 2007-05-12
Do just that. The command is in the dos/ directory.

---

