---
title: "Configure Camera?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-07-24
Hey, im trying to get this little camera to work as a webcam for my Ubuntu 7.04 but it reads the camera as a digital camera that takes only still pictures. Now i know i can use it as a webcam because before i converted to Ubuntu, i was on windows and i used this camera as a webcam.

[http://www.leapsandbounds.com/catalog/product.jsp?productId=6558#products](http://www.leapsandbounds.com/catalog/product.jsp?productId=6558#products)

And i went to Sakar.com (the maker of the cam) and they dont have a driver for linux. So is there a way i can configure this camera in the device settings or hardware settings or what ever to make it work as a webcam? thanks guys

---

### Post by w4ett on 2007-07-24
First lets see it your camera is recognized.  Plug in your camera and In the terminal  type:
```

lsusb
```

Please post the results (output) of the command.

---

### Post by ritterrav on 2007-07-24
I entered that and got this... 

> rav@Theplace:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
Bus 002 Device 002: ID 03f0:3b11 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
rav@Theplace:~$ 


I can see where the cam is, but how do i make it function as a webcam? this has built in memory (the cam) and ubuntu thinks its a digital cam and not a webcam.

---

### Post by w4ett on 2007-07-24
Go to Applications>Add/Remove and search for [COLOR="Blue"]Camorama Webcam Viewer[/COLOR]

Click and install it....we'll test if your cam can work out of the box.   They can be such tricky little devils...  :)

---

### Post by ritterrav on 2007-07-24
Ive tried that, and i get i get this error "Could not connect to video device (/dev/video0). Please check connections"

---

### Post by w4ett on 2007-07-24
Unfortunately there is not "out of the box" support for your cam.  I did some digging for you and came up with this link...there seems to be a Sourceforge project that might help you out:

[http://sourceforge.net/projects/stv0680-usb/](http://sourceforge.net/projects/stv0680-usb/)

there are further links on google...use the following search string:

[COLOR="Red"]2770:9120 linux driver
[/COLOR]

Sorry I can't be of further help, but it gets you on the road.  :)

---

