---
title: "Booting from USB on PowerMac G5 through OpenFirmware"
date: 2017-07-14
forum: Apple Hardware Users
---

### Post by leefernhere on 2017-07-14
Hello! 

I have created a USB installer of the PPC version of Ubuntu Mate. I am having trouble booting the usb from OpenFirmware, as I'm not quite sure how to read it. I understand that I must use a command such as "boot usb0/disk@1:2,\\yaboot" to boot off of the USB, but the command doesn't work, as I have tried it multiple times in multiple variations. I have taken a photo of my OpenFirmware list, with both commands being run ("dev / ls" and "devalias"), so I was wondering if anyone knows the proper command I should run to boot into it. Thanks! :)

[http://imgur.com/a/fC31S](http://imgur.com/a/fC31S)

1st image is "dev / ls" and 2nd image is "devalias" (Imgur)

---

### Post by slickymaster on 2017-07-14
*Thread moved to **Apple Hardware Users**.*

---

### Post by rsavage on 2017-07-14
Almost always I needed to use the OF command probe-usb before my USB devices were detected.  That would be my guess based on your dev / ls.  You have the devalias ud listed so you could try boot ud:2,\\yaboot

EDIT: on a second look you have a disk listed in your dev / ls so forget the probe-usb and just use the ud devalias

---

### Post by leefernhere on 2017-07-16
Thank you for your quick reply! It worked and I got into Ubuntu using the flag "live nouveau.noaccel=1" the first time, and realised I had to research something before going ahead with the install. 

I did my research and decided to go ahead with the install, except this time it didn't work, and now I just see a mouse pointer on a black screen. Not sure why it didn't work the second time. I even remade the USB but still no luck. If you know of anything, please do let me know. Specs below:

Nvidia Geforce 6600 (256mb ram)
Specs: 2GB PC2-4200 DDR2 RAM
PowerPC G5 2.7Ghz (2 cores)

---

### Post by rsavage on 2017-07-17
Btw, did you try holding down the option key on start up with the USB drive?  That should of worked on your machine.

Black screen - this is on an installed system?  Sounds like an old lightdm problem with 8 bit colour.  Nouveau probably not working and falling back to fbdev/offb.  Mistype on boot parameter?

---

### Post by leefernhere on 2017-07-18
I Tried and it didn't work, but OpenFirmware is easy so include fine with using that instead.
For the black screen with a mouse pointer, I haven't installed Ubuntu Mate yet, but I'm getting this black screen when trying to boot into the live USB. I tried the flag above and even the one suggested (I think it's "video=ofonly" or something) but they don't work.

---

