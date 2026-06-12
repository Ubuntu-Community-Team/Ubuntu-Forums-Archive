---
title: "How do I install my webcam?"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-10
I can't seem to get my webcam working at all. It is some cheap piece of rubbish from Argos so finding linux drivers for it is not likely to be easy.

Also - I installed gqcam but when I run that command nothing happens...surely something should at least pretend to happen?

---

### Post by rwabel on 2005-07-10
[QUOTE=gammyhand]I can't seem to get my webcam working at all. It is some cheap piece of rubbish from Argos so finding linux drivers for it is not likely to be easy.

Also - I installed gqcam but when I run that command nothing happens...surely something should at least pretend to happen?[/QUOTE]
 there are drivers around for logitech webcams. I've no idea what kind of webcam argos is. Or what is argos?
Google around to find out the driver it needs and the you should compile the driver. If that worked you should see something with gqcam.

---

### Post by gammyhand on 2005-07-10
[QUOTE=rwabel]there are drivers around for logitech webcams. I've no idea what kind of webcam argos is. Or what is argos?
Google around to find out the driver it needs and the you should compile the driver. If that worked you should see something with gqcam.[/QUOTE]
 Argos is a UK store :) The camera is unbranded.

---

### Post by rwabel on 2005-07-10
[QUOTE=gammyhand]Argos is a UK store :) The camera is unbranded.[/QUOTE]
 that makes it very complicated. Is there no indication about a name or what kind of chipset is inside. Another way would probably be to install it under windows and see what windows shows you!

---

### Post by polo_step on 2005-07-10
Interesting thread.  I've wondered what was needed to hook up my USB IBM/Xirlink webcam (KSX-X9903).

They're ubiquitous, so maybe there are Linux drivers for them, I dunno.

Any help will be appreciated.  Now I have DSL I might want to do something pinheaded like rig up a KittyCam so people can watch my cat sit in the window and lick herself.

OK, not a super priority, but It might be fun.

I found [this](http://www.linux-usb.org/ibmcam/) rather abstruse page, but I can't make heads or tails of it.  Really.

---

### Post by polo_step on 2005-07-10
[QUOTE=gammyhand]Argos is a UK store :) The camera is unbranded.[/QUOTE]
According to the above site, entering

$ cat /proc/bus/usb/devices

...will give you information about what the device actually is, if you know how to decipher it.

Here's what happens with mine:

T:  Bus=01 Lev=02 Prnt=05 Port=01 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=0545 ProdID=8080 Rev= 3.0a
S:  Product=USB IMAGING DEVICE
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=ibmcam
E:  Ad=81(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 1 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=ibmcam
E:  Ad=81(I) Atr=01(Isoc) MxPS=1022 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=   0 Ivl=0ms
I:  If#= 1 Alt= 1 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=1022 Ivl=0ms

Sorry if this is merely the blind leading the blind, but I'm working here on the theory that even if nobody who really knows the answer wants to help you for its own sake, they may not be able to resist helping you merely to point out how stupid I am.

Hey, whatever works, huh?

---

### Post by rwabel on 2005-07-10
[QUOTE=polo_step]According to the above site, entering

$ cat /proc/bus/usb/devices

...will give you information about what the device actually is, if you know how to decipher it.

Here's what happens with mine:

T:  Bus=01 Lev=02 Prnt=05 Port=01 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=0545 ProdID=8080 Rev= 3.0a
S:  Product=USB IMAGING DEVICE
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=ibmcam
E:  Ad=81(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 1 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=ibmcam
E:  Ad=81(I) Atr=01(Isoc) MxPS=1022 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=   0 Ivl=0ms
I:  If#= 1 Alt= 1 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=1022 Ivl=0ms

Sorry if this is merely the blind leading the blind, but I'm working here on the theory that even if nobody who really knows the answer wants to help you for its own sake, they may not be able to resist helping you merely to point out how stupid I am.

Hey, whatever works, huh?[/QUOTE]
 I've just shortly looked over the output! It seems that your webcam should be supported. It's model 2. As you have also written: KSX-X9903

as stated on their site:
<code>Support for all models (1, 2, 3, 4) is included in the driver that ships with Linux kernels starting with 2.4.12.  Previously you had to build the driver from CVS, but now this is not needed (or even recommended).</code>

Try to read also the [FAQ]("http://www.linux-usb.org/ibmcam/ibmcamFAQ.html") for troubleshooting.

I hope this helps a bit

---

### Post by polo_step on 2005-07-10
[QUOTE=rwabel]I've just shortly looked over the output! It seems that your webcam should be supported. [/QUOTE]
Yeah, that's sort of what I thought, though I don't get GnomeMeeting to find it (what Linux app works the first time though?).

dmesg gets me this (extracted):

usb 1-2: USB disconnect, address 2
usb 1-2: new full speed USB device using ohci_hcd and address 5
hub 1-2:1.0: USB hub found
hub 1-2:1.0: 4 ports detected
usb 1-2.2: new full speed USB device using ohci_hcd and address 6
Linux video capture interface: v1.00
drivers/usb/media/ibmcam.c: IBM PC Camera USB camera found (model 2, rev. 0x030a )
videodev: "ibmcam USB Camera" has no release callback. Please fix your driver fo r proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
drivers/usb/media/usbvideo.c: ibmcam on /dev/video0: canvas=352x240 videosize=35 2x240
usbcore: registered new driver ibmcam
NET: Registered protocol family 17
eth0: Media Link On 100mbps full-duplex
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [FUTS]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
eth0: no IPv6 routers present
drivers/usb/media/usbvideo.c: usb_submit_urb error (-1)
drivers/usb/media/usbvideo.c: usb_submit_urb error (-1)

...with a bunch of usb_submit_urb errors...

I'll check troubleshooting.

---

### Post by rwabel on 2005-07-10
[QUOTE=polo_step]Yeah, that's sort of what I thought, though I don't get GnomeMeeting to find it (what Linux app works the first time though?).

dmesg gets me this (extracted):

usb 1-2: USB disconnect, address 2
usb 1-2: new full speed USB device using ohci_hcd and address 5
hub 1-2:1.0: USB hub found
hub 1-2:1.0: 4 ports detected
usb 1-2.2: new full speed USB device using ohci_hcd and address 6
Linux video capture interface: v1.00
drivers/usb/media/ibmcam.c: IBM PC Camera USB camera found (model 2, rev. 0x030a )
videodev: "ibmcam USB Camera" has no release callback. Please fix your driver fo r proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
drivers/usb/media/usbvideo.c: ibmcam on /dev/video0: canvas=352x240 videosize=35 2x240
usbcore: registered new driver ibmcam
NET: Registered protocol family 17
eth0: Media Link On 100mbps full-duplex
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [FUTS]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
eth0: no IPv6 routers present
drivers/usb/media/usbvideo.c: usb_submit_urb error (-1)
drivers/usb/media/usbvideo.c: usb_submit_urb error (-1)

...with a bunch of usb_submit_urb errors...

I'll check troubleshooting.[/QUOTE]
 About the error message, I've no idea. sorry

as I stated some posting earlier, gqcam is a little webcam tool. Give it a try to see if the webcam is working

---

### Post by polo_step on 2005-07-10
Yeah, according to the troubleshooting page (above) and running --

$ cat /dev/video0 foo.dat

-- which produces a great wad of binary trash, indicating a healthy camera hookup, the camera is working, but GnomeMeeting just can't do anything with it:

==============================================
Error while opening video device /dev/video0

A moving GnomeMeeting logo will be transmitted during calls. Notice that you can always transmit a given image or the moving GnomeMeeting logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

There was an error while opening the device. Please check your permissions and make sure that the appropriate driver is loaded.
===============================================

---

### Post by polo_step on 2005-07-10
[QUOTE=rwabel] gqcam is a little webcam tool. Give it a try to see if the webcam is working[/QUOTE]
Will do. 

Thanks.

[Later]
gqcam --video /dev/video0

does indeed produce an image, though it's certainly no thing of beauty.  Lots of errors show up in the terminal, about a million of these --

Error reading image...
ioctl (VIDIOCSWIN): Invalid argument
ioctl (VIDIOCSWIN): Invalid argument

-- but this is a start, anyway!  :-P

[Later] xawtv likes it even less, though a brief picture does show up:

anonymous@beatdown:~$ xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
WARNING: v4l-conf is compiled without DGA support.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to typ e FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=7): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=15): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=9): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=4;width=8;format=5): Invalid argument
game over

---

