---
title: "webcam Help"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jhyatt7823 on 2007-11-17
I can't get my logitech QC for notebooks working on Gusty.  Can anybody that got this working give me some insight please I am very frustrated!

---

### Post by anemptygun on 2007-11-17
Can you tell us more? What are you planning on using it for?

---

### Post by profXavier on 2007-11-17
First, run the command [FONT="Times New Roman"]lsusb[/FONT], so we know what type of camera your using, then it makes it easier to find the correct driver for the device.  Its a first step...

---

### Post by cklinux on 2007-11-18
from lsusb
Bus 002 Device 010: ID 046d:08c5 Logitech, Inc.
I have video4linux instaled as well as camorama and webcam monitor but my camera
doesn't work with Im
as far as I have seen I probably must create some sort of virtual device at /dev/video0
to point to the above usb as almost all programs search at /dev/video0 for my webcam.
If indeed that is the solution how I do it?:confused:

---

### Post by hutxubix on 2007-11-18
I am having the same problem. From lsusb I get

Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 004: ID 045e:00b4 Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000

---

### Post by little_penguin on 2007-11-18
@cklinux:

It appears from this list:

[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

that your webcam model, according to its unique ID 046d:08c5, is the Logitech Quickcam Pro 5000 and needs the UVC driver.

The Linux UVC driver can be downloaded here:

[http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")

---

### Post by little_penguin on 2007-11-18
@hutxubix

For the Logitech Quickcam Express, maybe this site will help:

[http://qce-ga.sourceforge.net/]("http://qce-ga.sourceforge.net/")

---

### Post by little_penguin on 2007-11-18
@jhyatt

Please post the output of the command lsusb so we can see the unique ID of the webcam model.

---

### Post by jhyatt7823 on 2007-11-24
Bus 002 Device 002: ID 093a:260e Pixart Imaging, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


this is the output I get. Im actually do not have the logitech one anymore

---

### Post by little_penguin on 2007-11-24
In mxhaard's list, it says your webcam with the ID 093a:260e requires the gspcav1 driver.

You can download it here:

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)

---

### Post by jhyatt7823 on 2007-11-24
Is there installation instructions?

---

### Post by little_penguin on 2007-11-24
After downloading the file, open a terminal and cd to the directory you downloaded it to and type the following commands:

1. tar xvzf gspcav1-20070508.tar.gz

2. cd gspcav1-20070508

3. sudo make

4. sudo make install

---

### Post by jhyatt7823 on 2007-11-24
I got the camera to work with skype but the micro phone was not working.  Now neither are working again :-(

---

### Post by little_penguin on 2007-11-24
Hmmm, ok it's encouraging if the webcam worked, albeit only for a short time, at least we know it *does* work. A mystery to me why it's suddenly stopped though. 

As for the sound, have you checked the sound mixer settings? On my Kubuntu system, I have a loudspeaker icon called Kmix, there are a bunch of settings in there you need to check, both input and output settings, microphone, etc., make sure they are set correctly and not muted. On Ubuntu it will be something similar I think.

Then experiment with the sound settings in Skype in Options / Sound Devices, make sure it's set to your sound card.

What kind of headset have you got? Are you using a laptop (I'm basing this supposition on the webcam for notebooks you bought originally but have since returned)? If so, what make and model is the laptop?

---

