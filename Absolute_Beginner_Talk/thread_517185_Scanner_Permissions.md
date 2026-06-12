---
title: "Scanner Permissions"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-08-04
I have a  problem using my scanner.

With lsusb I can confirm that the device is identified

```
Bus 005 Device 002: ID 03f0:2305 Hewlett-Packard ScanJet 3970c
```

and with scanimage -L  I can see that the device is seen by applications.

```
device `hp3900:libusb:005:002' is a Hewlett-Packard RTS8822 chipset based flatbed scanner
```


Xsane or other scanning programs shows the error 

```
Unknown message: scanimage: open of device hp3900:libusb:005:002 failed: Access to resource has been denied
```

I am a member of the scanner group and saned.

How do I allow access to the scanner?

---

### Post by stevebakerj on 2007-08-04
Does it have the right permissions

From the sample output you give the USB connection is at 005/002.
change the permissions with:

chmod 0666 /proc/bus/usb/005/002

---

### Post by grobar on 2007-08-04
Hi do you have this file ?
[http://alexaubuntu.googlepages.com/PS1Dfw.usb](http://alexaubuntu.googlepages.com/PS1Dfw.usb)

If not download it and copy it to all 4 directories

usr/local/share/sane/gt68xx
usr/local/share/sane/xsane
usr/share/sane/gt68xx
usr/share/sane/xsane

If you don't have these directories then you'll have to make them:

open terminal and type " mkdir  usr/local/share/sane/gt68xx " and so on for ever dir...

and copy the file in all 4 of them, start applications-graphics-xsane !

---

### Post by expatCM on 2007-08-04
stevebakerj - did that and the scanner now works.  Thanks for the fix :)

grobar - thanks for your suggestion.  I just had a look at the source page ...  and then I was wondering what the file does please?

---

