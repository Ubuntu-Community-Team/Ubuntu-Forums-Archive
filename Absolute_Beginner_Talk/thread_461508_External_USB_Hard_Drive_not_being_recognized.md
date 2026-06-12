---
title: "External USB Hard Drive not being recognized"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by scooter3k on 2007-06-01
So, I have a Fantom Drives 250 gb external usb hard drive, FAT32 formatted, with all of my data on it (college work, pictures, music, etc...) and it worked fine (mounted on its own and stuff) before I went on vacation 2 weeks ago.  Now I'm back and it won't mount!  I tried on my friend's windows pc also, won't mount there either.  (In windows it shows up in the device manager with an exclamation point, and gives the error: "This device cannot start. (Code 10)")

It isn't showing up in /dev/sd* where it should normally be, right?  I tried running udevmonitor in a terminal, then turning on the external drive, and this is what I got:

```


udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UEVENT[1180740309.193124] add      /devices/pci0000:00/0000:00:10.1/usb2/2-2 (usb)
UEVENT[1180740309.193271] add      /class/usb_endpoint/usbdev2.2_ep00 (usb_endpoint)
UEVENT[1180740309.194454] add      /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0 (usb)
UEVENT[1180740309.194555] add      /class/scsi_host/host2 (scsi_host)
UEVENT[1180740309.194589] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740309.194622] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740309.194654] add      /class/usb_device/usbdev2.2 (usb_device)
UDEV  [1180740309.195875] add      /devices/pci0000:00/0000:00:10.1/usb2/2-2 (usb)
UDEV  [1180740309.218112] add      /class/usb_endpoint/usbdev2.2_ep00 (usb_endpoint)
UDEV  [1180740309.346073] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740309.463228] add      /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0 (usb)
UDEV  [1180740309.465883] add      /class/scsi_host/host2 (scsi_host)
UDEV  [1180740309.479954] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740309.573331] add      /class/usb_device/usbdev2.2 (usb_device)
UEVENT[1180740319.952767] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740319.952810] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740319.952821] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740319.952830] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740319.955452] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740319.967252] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740319.969227] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740320.058727] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740330.212538] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740330.212584] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740330.212595] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740330.212604] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740330.215210] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740330.217519] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740330.232870] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740330.318399] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740335.472394] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740335.472444] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740335.472454] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740335.472463] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740335.475148] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740335.477584] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740335.489812] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740335.500162] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740345.733284] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740345.733334] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UEVENT[1180740345.733344] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UEVENT[1180740345.733354] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740345.736652] remove   /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740345.739229] remove   /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)
UDEV  [1180740345.751519] add      /class/usb_endpoint/usbdev2.2_ep02 (usb_endpoint)
UDEV  [1180740345.842609] add      /class/usb_endpoint/usbdev2.2_ep88 (usb_endpoint)

```

There is no line that says something like add@/block/sd... which it normally should do, I think.

So, the computer is getting some sort of signal from it.  I'm hoping it isn't damaged somehow, because the data on it is really important to me.

Also,  sudo fdisk -l with the drive powered on gives:

```

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

```

fdisk - l gives the same thing with the drive powered off also =/

There are no crazy noises coming from the drive that sound it is grinding away or anything.

Is there any way I can backup the data on the drive with it acting all crazy and bad like this?  I hope I'm not boned, cuz I don't have a backup of my data :(

My guess is that the circuitry got damaged somehow since the drive sounds fine...I am going to try and find another USB cable to plug it in with, or maybe another power adapter too and see if either of those fix it.

Thanks for any help you can provide in advance!!! :D
-Scott

---

### Post by smoker on 2007-06-01
hi, not sure about this one (fantom), but some external hard drives can easily be removed from the caddy, inside the last one i had, it was an ide drive that connected to a recessed ide port held on a circuit card that the usb connection ran from to the exterior. i could remove the drive and connect it as an internal drive on an ide channel. perhaps if yours is the same or similar you could slave it your pc ide and check it from there...

best of luck

---

### Post by Lucifiel on 2007-06-01
Hmmm... I would check to see if your Bios supports booting from usb and if so, get Spinrite and run it.

Spinrite will then attempt to fix your drive. 

Or maybe you could try ddrescue.

---

### Post by scooter3k on 2007-06-02
sweet action!! i opened that sucker up, and out popped a hard drive!  i hooked it up as a slave inside my computer, it mounted, voila!  my data!!

thanks a bunch :)
-scott

---

### Post by Lucifiel on 2007-06-02
In which case, I'd say your casing has gone kaput. :p

---

