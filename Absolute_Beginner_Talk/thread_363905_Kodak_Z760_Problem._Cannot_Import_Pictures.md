---
title: "Kodak Z760 Problem. Cannot Import Pictures"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by ADZ on 2007-02-17
Whenever I connect my camera, I get the following message:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I cannot import any of my pictures.
If anyone knows thanks :)

---

### Post by yager on 2007-02-17
Your problem was so specific that I had to try with my Z760 camera.  I have replicated the exact same error message.  I have downloaded pictures from my Z760 under Dapper and Breezy in the past.  I have not tried to download anything recently under Edgy so it must be something that recently changed.

I just confirmed that I can access the camera from my son's computer that has Dapper Drake.  Ubuntu is or at least was able to work with this camera.

Okay, here are some technical issues that are different between the computer that works and does not work.

The working system:
[INDENT]256MB Ram, 2GHz Intel processor
Has a USB1 port.  Camera downloaded just fine.
Running Dapper Drake
Dapper is installed on hda1
[/INDENT]
Non-working system that worked with Dapper Drake:
[INDENT]1 GB Ram
2.4 GHz processor
USB2.0 ports.  Camera is recognized when connected but does not load driver when I choose to import pictures.
Running Edgy Eft
Ubuntu is installed on a USB hard driver connected to another USB2 port.  Same configuration as in the past.[/INDENT]

What is your hardware configuration?

Dude I have found the answer.
The source came from this thread.
[http://ubuntuforums.org/showthread.php?t=286730&highlight=kodak](http://ubuntuforums.org/showthread.php?t=286730&highlight=kodak)

The exact sequence of commands that I did were as follows.  Which summarizes that thread.
1. Open the terminal. Attach the camera and turn it on. Don't bother selecting import pictures.
2. Enter ```
lusb
```
The output will look something like this.
```
Bus 004 Device 003: ID 0bc2:0502 Seagate RSS LLC 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 010: ID 040a:0581 Kodak Co. 
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```
3. Take note of the line that has Kodak Co. on it.  This is your camera.  The ID info will be required in Step 5.
4. Next enter  ```
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```
5. Scroll to the bottom of the file and enter this line right before the last line in the file.
```
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0581", MODE="0660", GROUP="plugdev"

```
The idVendor are all of the digits before the colon from step 3.  The idProduct are all of the digits after the colon in step 3.  You may have to adjust.
6. Save the changes to the file. Turn off the camera and cancel the import dialog box if it is still displayed.
7. Enter this final command.```
sudo /etc/init.d/udev restart

```
8. Turn the camera on and everything should work just perfectly.

If you have any other problems with this, please direct your questions to the source thread that I found.  They are much more knowledgeable about these things than I.

---

### Post by ADZ on 2007-02-18
Thank you sooo much! It WORKS!!! :KS You're the best!

---

