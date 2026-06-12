---
title: "USB Port and proper use?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by kfehr911 on 2007-04-28
Well I don't properly know how to use the usb ports so that I can transfer photo's to F-spot.  When I plug in the camera I get this message when I try to import the photo's. 
 
[COLOR="Blue"]An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.[/COLOR] 

 Any on line reading or a simple way that I can import these files.  I don't like to mess around settings with out a proper out line of what I want to do.  I also couldn't  delete files off a flash drive until tonight.  What do I have to do so that I can have the permissions and access  to the files through the usb port.

---

### Post by Xarok on 2007-04-28
Are you able to access the camera through the icon on the desktop and copy the files to the desktop and then load them into F-spot?

---

### Post by kfehr911 on 2007-04-28
No.  There is no icon on the desk top and I believe that it is a permission problem. I don't know where to start. As I said before I know that I could make thing worst is I don't have any direction.:confused:

---

### Post by dondad on 2007-06-07
I have exactly the same problem. Funny thing is that it used to work. I did find that I could use gtkam if I ran it at root with gksudo, but then the pictures are all owned by root. 

I am also olooking for someplace to go looking for a solution. I have done a bunch of searches, and everything that I find, shows up as OK on my box. I managed to break the HAL once, but got it back ;-)

---

### Post by candtalan on 2007-06-07
FWIW
 I have good results with digikam (I use kubuntu, so I guess some kde libraries will also be used if you install digikam)

---

### Post by dondad on 2007-06-07
I have tried digikam and also gtkam. Neither one will work. The camera is detected, but I cannot communicate with it.

---

### Post by candtalan on 2007-06-08
> **dondad said:**
> I have tried digikam and also gtkam. Neither one will work. The camera is detected, but I cannot communicate with it.

I use kde mostly (kubuntu-desktop package) and when the camera is connected, it gets automatically mounted and an icon appears on the screen. 
If I then right click on the icon, I get a menu which includes Actions>'Digikam detect and download'. 
Alternatively, when the camera is first connected, a window appears 'A new medium has been detected, what do you want to do?' and options include 'Digikam detect and download'
hth

---

### Post by Bloch on 2007-06-08
Not all cameras work. I had a camera before and ubuntu could detect the make and model but was unable to work with it. Other less obscure cameras worked fine.

Do a google search of your model number + linux and see if it works at all.

If not you might have to use a card reader - you take the memory chip out of the camera and slip it into the device. All kinds of memory cards can be read

---

### Post by dondad on 2007-06-08
My camera is a common one that used to work. it was detected fine, but it looks like there is/was a permission problem with using the usb port. I finally fixed it by uninstalling the photo library, everything I could find associated with it,  and the digicam/gtcam, then reinstalling everything. In my searches I found several threads with this same problem and some bug reports talking about it, although none of the fixes suggested corrected my issue. The bug reports was where I got the idea for what to uninstall and redo. I am very new to linux and was fairly proud of myself in that I only broke the system once while working on this problem ;-)

---

