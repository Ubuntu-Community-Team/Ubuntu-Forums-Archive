---
title: "from MacBook USB to Samsung Netbook"
date: 2010-12-20
forum: Apple Hardware Users
---

### Post by olivo on 2010-12-20
Dear All, 
I am new to the forum and hope this post is correctly placed. Please remove or replace it
if this is not appropriate. 

I have a MacBookPro and a netbook Samsung NC10. 
I destroyed the OS on the netbook and would like to restore it with Ubuntu by using a USB stick. 

I created the USB-Ubuntu disk by following the instructions on: 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

selecting USB and Mac (the only working computer I currently have): 

    hdiutil convert -format UDRW -o ubuntu-8.04.3-desktop-i386.img ubuntu-8.04.3-desktop-i386.iso 
  mv ubuntu-8.04.3-desktop-i386.img.dmg ubuntu-8.04.3-desktop-i386.img
  diskutil unmountDisk /dev/disk2
   sudo dd if=./ubuntu-8.04.3-desktop-i386.img of=/dev/rdisk2 bs=1m
   diskutil eject /dev/disk2

whithout any error message, 


then I plugged the USB stick on the Samsung Netbook and tryed to boot from USB drive
but I get the message "Operating System not found" 

I have no idea of what went wrong, could you please help?

thanks in advance, 
Olivo

---

### Post by iponeverything on 2010-12-20
reboot, go into the bios and change the boot device to be the usb.

---

### Post by olivo on 2010-12-20
> **iponeverything said:**
> reboot, go into the bios and change the boot device to be the usb.

thanks for the answer, 
as I wrote the OS is broken and no boot (and reboot is possible) on the Samsung box. Moreover, 
when selecting the USB as boot device, I get the above error message.

---

### Post by slooow on 2010-12-20
The BIOS should not be affected by a broken OS. You might have to press escape, F8 or another key to bring the bios interface up. The correct key is shown on the screen when it boots.

---

### Post by olivo on 2010-12-20
Sorry folk, I was not clear. 
I am able to select the USB stick for boot. 
The problem is that, after selecting the USB stick I get the error "Operating System not found"

---

### Post by slooow on 2010-12-21
In that case there seems to be something wrong with usb stick. Not bootable? Bad sectors? 
Try the stick first on your mac machine if that is possible.

---

### Post by futn001 on 2010-12-22
Look at the next remove U disk at startup, or not, it can only get  after-sale check to see if the most likely hardware problems

---

