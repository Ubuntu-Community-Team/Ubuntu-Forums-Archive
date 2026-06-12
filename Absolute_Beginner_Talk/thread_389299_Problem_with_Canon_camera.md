---
title: "Problem with Canon camera"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by bootsbradford on 2007-03-20
I am using ubuntu 6.10. I have had no trouble until today plugging in my digital camera and then downloading pictures. The last time I did this was probably a month or so ago.

However, today I am getting an error message:

***"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."***

Can anyone offer me any assistance? There is nothing else running that I can see.

It is frustrating that such a basic operation suddenly doesn't work!

---

### Post by chaplanger on 2007-03-20
I've had the same problem.  I found these directions today in another thread and it worked!  (evidently something in one of the updates inadvertently changed the "BUS" line).  Good luck!

> 
Binary package hint: libgphoto2-2
The file /etc/udev/rules.d/45-libgphoto2.rules says in line 3:
BUS!="usb*", GOTO="libgphoto2_rules_end"
while recenly updated udev doesn't produce BUS properties in corresponding event. Thus this line makes the whole file useless, because BUS!="usb*" is never true.
Something like
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
instead would work.


You will need to go into terminal and copy & paste:

> sudo gedit  /etc/udev/rules.d/45-libgphoto2.rules

then follow the instructions above and comment out the line: 
BUS!="usb*", GOTO="libgphoto2_rules_end" so that it looks like this: 
> # BUS!="usb*", GOTO="libgphoto2_rules_end"
below this line then cut and paste:  

> SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

save the file and now your camera should be recognized.

---

### Post by wylie98 on 2007-04-18
Thanks, I had exactly the same problem and this worked perfectly for me. I had no idea which update had done this since the last time i used the camera was a few months back.

Thanks 
Wylie

---

