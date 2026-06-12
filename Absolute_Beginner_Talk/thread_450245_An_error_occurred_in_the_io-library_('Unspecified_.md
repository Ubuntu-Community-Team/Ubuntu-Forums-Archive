---
title: "An error occurred in the io-library ('Unspecified error'): Could not query kernel dri"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by kfehr911 on 2007-05-21
This was what I had received through a forum about how to correct the problem I was having getting camera to import photos.  I had done the following 

[COLOR="Blue"]Open a Terminal and type:


sudo gedit /etc/udev/rules.d/45-libgphoto2.rules


Comment out the third line by add a number sign # and add insert DIRECTLY beneath it this:


SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"


Save the file and close Gedit.


When you’re done editing the first five lines should look like:


# udev rules file for libgphoto2 devices (udev < 0.9
#
#BUS!=”usb*”, GOTO=”libgphoto2_rules_end”
SUBSYSTEM!=”usb_device”, GOTO=”libgphoto2_rules_end”
ACTION!=”add”, GOTO=”libgphoto2_rules_end”



Now, restart udev:


sudo /etc/init.d/udev restart[/COLOR]

This worked great in solving the problem for the Sony PowerShot A80 I have but what about the Panasonic DMC-FX8 that my friend has.  I'm getting the following error.

[COLOR="Red"]An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device.[/COLOR]

At first it  loads  the  drivers from usr/libphoto/libphoto2.3.0.  It finds a driver but doesn't connect.  I have downloaded through aptitude both gphoto2 and gphotofs and that has not corrected the problem.  What step am I missing? What else will I need to do so that I can import these photos from this camera?  It is very important to me because I will be using two or three different cameras in the near future.   Please help me so that I will not be hung up every time I use a different camera. Thanks and Cheers

---

### Post by defe007 on 2007-07-18
Hey, I am also wondering about this problem.  I have a Panasonic DMC-TZ3 and it worked with Ubuntu before.  I don't think I have changed anything but now I'm getting this error: "An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device." whenever I try to import.  The device will not mount.  Help please?

---

### Post by defe007 on 2007-07-18
Ooops, sorry for the double post.

---

### Post by rare HERO on 2007-08-05
I've got the same error...

---

### Post by essexman on 2007-08-05
Yes

This is a bug - I'm using Dapper and my Kodak CX7530 has worked fin for over a year until now - I'v tried going bac a kernel I will go back more

---

### Post by essexman on 2007-08-05
The bug is that if there is a corrupt file on the camera libgphoto will not download anything
install gphoto2
then type at a command line: ```
gphoto2 --port "usb:" --camera "Kodak CX7530" --get-all-files
```

Substituting your camera name

---

### Post by tuesday20102001 on 2008-06-20
sorry for confusion

---

### Post by tuesday20102001 on 2008-07-15
sorry for the confusion, the command works if the above dependency is installed.

---

