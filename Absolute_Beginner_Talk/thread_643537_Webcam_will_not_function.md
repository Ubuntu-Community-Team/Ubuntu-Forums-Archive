---
title: "Webcam will not function"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by diaz028 on 2007-12-17
I have plugged in the USB cam 'Logitech Quickcam Pro 3000'. I searched and found PWC drivers which people say work fine. I followed the instructions, and nothing seems to work.

[http://www.seismo.ethz.ch/linux/webcam.html](http://www.seismo.ethz.ch/linux/webcam.html)

Im trying everything but I get stuck @ 

Code
> diaz@diaz-desktop:~$ cd '/home/diaz/Desktop/pwc-10.0.11' 
diaz@diaz-desktop:~/Desktop/pwc-10.0.11$ cp -p /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/pwc.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/pwc.ko_orig
cp: cannot stat `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/pwc.ko': No such file or directory
diaz@diaz-desktop:~/Desktop/pwc-10.0.11$ 


Am I doing this all wrong?

Thanks 

-D

---

### Post by spiderbatdad on 2007-12-17
the problem suggests a typo or incomplete path to file eg, cp: cannot stat `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/pwc.ko': No such file or directory

---

### Post by diaz028 on 2007-12-17
[http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html](http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html)

Maybe there would be a better way here? I am still having a hard time with this... Can anyone simplify this for me? Thanks

-D

---

### Post by spiderbatdad on 2007-12-17
depends on what you're trying to do. there is a program in Add/Remove called camorama if you enable the all programs feature. It allows basic cam functionality Also have you tried navigating the file system to the directory it says doesn't exist, so that you can get the path entered correctly?

---

### Post by diaz028 on 2007-12-18
thanks i'll give it a shot!

-D

---

### Post by freddybob on 2007-12-18
Can anyone recommend a webcam that will work out-of-the-box in Ubuntu Gutsy?

---

### Post by philinux on 2007-12-18
To get the correct driver you need the vendor code of the cam.

Post the output of 

[FONT="Courier New"]**lsusb**[/FONT]

---

### Post by diaz028 on 2007-12-18
> **philinux said:**
> To get the correct driver you need the vendor code of the cam.

Post the output of 

[FONT="Courier New"]**lsusb**[/FONT]

Code:
> diaz@diaz-desktop:~$ lsusb
Bus 005 Device 003: ID 046d:c20d Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
diaz@diaz-desktop:~$ 


-D

---

### Post by siciliancasanova on 2007-12-18
So you guys know I bought a Logitech Quickcam Communicate Plus STX 3 days ago and it works out of the box on gutsy and hardy.

---

### Post by freddybob on 2007-12-19
> **siciliancasanova said:**
> So you guys know I bought a Logitech Quickcam Communicate Plus STX 3 days ago and it works out of the box on gutsy and hardy.

thanks sicilian, good to know

---

### Post by philinux on 2007-12-19
You're out of luck with the generic driver for this cam then. I just checked the vendor code. I'm using a logitech quickcam messenger.
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Back to the drawing board ....

---

