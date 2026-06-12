---
title: "digital camera picture transfer"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-07-25
I have a kodak easyshare dx6440 digital camera and am having trouble transfering my pictures from my camera to my computer.  A kodak installation cd came with the camera, and worked fine in windows, but I'm fairly certain it will not be compatible with linux.  The cord from the camera is a simple usb cable. 

Any ideas?

---

### Post by ndyguy on 2006-07-25
You could try the cd using Wine, or you could try to find a package on synaptic.  If you have more problems please include more info. like what you've tried already, any error messages you've gotten, what format the pics are, etc.

---

### Post by robins_web on 2006-07-25
Try digikam, available via synaptic:

Digikam: digital photo management application for KDE
Digikam is an easy to use and powerful digital photo management
application, which makes importing, organizing and manipulating,
tagging and searching digital photos a "snap".  An easy to use
interface is provided to connect to your digital camera, preview
the images and download and/or delete them.

Digikams builtin image editor makes common photo corrections
a simple task.  It is extensible via the plugins provided by the
digikamimageplugins package.

Digikam can also make use of the KIPI image handling plugins to
extend it's capabilities even further for photo manipulations,
im- and export, etc.  The kipi-plugins package contains many
very useful extensions.

Homepage: [http://www.digikam.org](http://www.digikam.org)

---

### Post by djsroknrol on 2006-07-25
Gthumb, which is a native Ubuntu program should work...try:

Applications>Graphics>Gthumb

with the camera plugged in and see what happens..it should be like my wie's Sony, and show the contents of the camera..

---

### Post by sabredog on 2006-07-25
Gthumb automatically finds my Kodak DX6490, Canon A410, Fuji 2650 and my old Kodak Dc290. 

I must admit I have not tried my daughters DX6440 as yet, but based on the above, it should work a treat.

---

### Post by echo $USER on 2006-07-26
I have a kodak cx7300.  All i have to do is plug it in, turn it on, let linux recognize, and transfer.  I use digiKAM to organize my photos.

---

### Post by missmoondog on 2006-08-05
i have a kodak cx7530 that keeps giving me an error of bad paramaters. the computer can see the camera and i can even get so far as to have previews load, but pics won't download from the camera. i'm using digicam.

edit:
problem solved for me. uninstalled digikam and installed gthumb. click! there's the pics!! just like it should. :-D

---

### Post by patrick295767 on 2006-08-05
> **oscar78 said:**
> I have a kodak easyshare dx6440 digital camera and am having trouble transfering my pictures from my camera to my computer.  A kodak installation cd came with the camera, and worked fine in windows, but I'm fairly certain it will not be compatible with linux.  The cord from the camera is a simple usb cable. 

Any ideas?

  
Usually most camera works in Linxu.
Take care wittth permissiosn ! That can be the trick
(/proc/ ... usb)
 
If you have dapper, should be okay.
  
If sudo dmesg 
says it saw it ... You will have possibility to download usually.
  
Try for instance the kde camera programs (forgot the name how possible?), that's easy to download the pictures.
  
It should be working, even better than windows !
  
Cheers !

---

### Post by slimdog360 on 2006-08-05
> **ndyguy said:**
> You could try the cd using Wine, or you could try to find a package on synaptic.  If you have more problems please include more info. like what you've tried already, any error messages you've gotten, what format the pics are, etc.
wine cant emulate the drivers of a device.

but anyway, if you havent already tried the camera should just automatically be found and work when you plug it in. I couldnt imagine why it wouldnt.

---

### Post by Psquared on 2006-08-11
All these programs seem to work better in linux than Windows. I had a very difficult time installing the drivers and software to get the pictures from my camera in XP. Digikam did it all very easily. I find that odd but good for linux and bad for Windows.

---

### Post by davegb2 on 2006-08-12
I have a Kodak LS743. The only way I can transfer is with Konqueror. It's very slow though so I show the photos in list view (not preview), then I copy them to the hard-disk. Also, I think there's a 'camera'  system setting in preferences and I selected my camera there (not sure if you have to do this though).
dave

---

### Post by Cyraxzz on 2006-09-01
Would this function on my Canon Digital IXUS 60?

It also need "digital camera picture transfer".

---

### Post by Declan Moriarty on 2006-09-01
I have a Sony DSC-N1.  I had to change the USB mode setting in the menu of the camera when pluged into the computer from "Auto" to "PTP" then Ubuntu detected it.  There might be a similar setting on your camera.  After Linux Detected it gThumb started automatically and I was able to download some pictures onto another USB stick.

---

