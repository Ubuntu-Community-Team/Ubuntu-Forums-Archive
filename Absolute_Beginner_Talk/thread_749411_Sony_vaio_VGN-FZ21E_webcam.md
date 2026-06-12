---
title: "Sony vaio VGN-FZ21E webcam"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by borgrodrick on 2008-04-08
Hi I wish to install a driver for my webcam...  lsusb gives me :

Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  


does anyone knows where to find this driver??? 

Thanks

---

### Post by linuxwizard on 2008-04-08
This is the driver you need. Your cam is listed as supported.

[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

---

### Post by borgrodrick on 2008-04-09
after installing the driver do I need to install some program that actually uses the webcam?

---

### Post by linuxwizard on 2008-04-09
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

You could install Camorama or Cheese.

---

### Post by borgrodrick on 2008-04-10
hey thanks for your reply... I think I either got the wrong driver or installed it wrong because all I saw in Ekiga was some grey pictures. The light of the motion eye camera is being turned on though.

---

### Post by linuxwizard on 2008-04-10
Did you work with the settings like I posted to do ? Also when you have Ekiga open along the bottom there is a video tab click on it, their you can adjust color, brightness.

---

