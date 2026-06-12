---
title: "Buslink L-series usb external hard drive question"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by newbdave on 2007-10-17
Hello all,

I have a Buslink L-series(yellow caps) external hard drive. When I plug the usb in and turn on the power.....nothing happens. On an XP system it requires a driver to work. I don't know if this is the same problem. If it is do I use wine to install the driver? Any help would be appreciated.

---

### Post by overdrank on 2007-10-17
> **newbdave said:**
> Hello all,

I have a Buslink L-series(yellow caps) external hard drive. When I plug the usb in and turn on the power.....nothing happens. On an XP system it requires a driver to work. I don't know if this is the same problem. If it is do I use wine to install the driver? Any help would be appreciated.

Hi and welcome, can you use the command ```
lsusb
``` in the terminal located under applications,accessories. And see if it is listed there.

---

### Post by newbdave on 2007-10-17
Yes, this is what I get.




Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 009: ID 067b:2307 Prolific Technology, Inc. PL2307 USB-ATAPI4 Bridge
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c50a Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
david@david-desktop:~$

---

### Post by skibum58 on 2007-10-20
I have the same drive, Buslink yellow L-series 60 GB which I could really use on my Feisty / Sony Vaio notebook.  I plugged it in, got a heartbeat from the lsusb command (basically the same as Newbdave), but no auto-recognition.  Granted this thing is old, and was using some sort of Bridge to IDE which requires special drivers on Windows.

Took me a couple hours, but following this trail I was able to get the drive recognized:

(1)  Read [http://www.qbik.ch/usb/devices/showdev.php?id=605](http://www.qbik.ch/usb/devices/showdev.php?id=605) .  It leads you to 
(2)  [http://bravin.home.cern.ch/bravin/usbide/usbide.html](http://bravin.home.cern.ch/bravin/usbide/usbide.html) (THANK YOU Enrico Bravin)
(3)  Download the latest build usbide-2.1.tar.gz  (latest - fixes for kernels >= 2.6.1)
(4)  Unpack/Extract somewhere.  You may have to Alt-F2 "gksudo Nautilus" if you want to get the  directory which is created (usbide) out of your home directory or desktop.
(5)  Navigate to the usbide directory and read the Install file.  Follow the instructions.  I did not have to solve any dependencies or anything, just ran sudo Make and sudo Make Install.
(6)  It ran without throwing errors.  I had my Buslink turned off, so contrary to the installation instructions there was no UDA listed in /dev/.
(7)  Rebooted (force of habit), took a deep breath, turned on the Buslink, et voila, a listing for UDA and UDA1 popped up.
(8)  Terminal | sudo mkdir /media/buslink
(9)  Terminal | sudo mount /dev/uda1 /media/buslink
(10)  Navigated to /media/buslink and there it was in all its shining USB 1.1 glory.

It was read only at that point but I am running the NTFS configuration tool.  Fired it up and rendered the disk writable.

About to move from Feisty 7.04 to 7.10, which will probably bollux up the whole thing, but this is interesting stuff.

skibum

---

### Post by newbdave on 2007-12-04
I finally got it to work following your instruction. Thanks alot !!

---

### Post by sitmex on 2008-01-25
Great, thanks for the instructions, followed, no issues, and have it working.

I have been looking for a solution as simple as that.

Thanks Again

Oscar
Guadalajara, México.

---

