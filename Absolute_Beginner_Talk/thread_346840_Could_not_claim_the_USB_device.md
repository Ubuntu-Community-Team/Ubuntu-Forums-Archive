---
title: "Could not claim the USB device"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Vikas Tiwari on 2007-01-26
Hello everyone

I have started using Ubuntu very recently and am very delighted with the performance of this operating system. However, being a new user, I am experiencing some difficulties in operating it.

I recently made a few videos from my Kodak Digital Camera and wanted to save them in my computer. Now whenever I connect my camera to my laptop, I am being asked if I wanted to import photos from the camera.  However, when I click on the option "import photos", I get the following message "An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

I have tried all the image viewers available in Ubuntu but I can't import my photos or videos. I request the forum to help me in resolving this situation.

Sincere regards
Vikas

---

### Post by maneesh77 on 2007-01-26
I dunno why it's saying that. I got a kodak c663. It seems to work fine with ubuntu. 
When I do have problem with the USB it's usually a loose connection to my USB device :-)

---

### Post by yigal.weinstein on 2007-01-26
There is a bug.  I just got a beautiful Kodak z710 digital camera today an hour ago and it is working perfectly now though.
 The bug is not really a bug but simply giving proper permissions to gThumb to mount/download your photos. 

1. In a terminal please do the following:
```
lsusb
```

2. find the line of the output that contains Kodak in it and copy "copy:this:" see bellow,
```
Bus 0ab Device 0cd: ID copy:this Kodak Co.
```
for example my beautiful Z710 has the following line:
```
Bus 001 Device 012: ID 040a:05b3 Kodak Co.
```
so I would copy "040a:05b3" for the next step.

3. ```
sudo vim /etc/udev/rules.d/45-libgphoto2.rules
```

I use vim but you can use what ever you are comfortable with, I suggest gedit if you are a Linux newbie.

4. on a new line copy "copy:this" this way:

```
SYSFS{idVendor}=="copy", SYSFS{idProduct}=="this", MODE="0660", GROUP="plugdev"
```

for example my camera entry looks like,
```
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05b3", MODE="0660", GROUP="plugdev"
```

you must now restart udev in order for it to take notice of the changes you made. So type,
```
sudo /etc/init.d/udev restart
```

5. You should now be able to import what you want - I can :D .  If you have problems I have subscribed to this message so don't hesitate to reply.

I have a screenshot of something similar to what you should see after you reattach your camera after the above steps ( - I have already decided to use one of my pictures as a desktop background - at least for today).

Note, this "problem" has already been reported as a bug,
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146")

---

### Post by myke on 2007-02-04
Edit of my original post ...

This worked for me.  I made an error editing the libgphotos2.rules file with respect to the settings for my camera but once I corrected that, it works just fine.   Thanks for your detailed steps for help.   Both gThumb and digikam are working well for me now and importing my photos is back online.

Thanks again.

---

### Post by myke on 2007-03-11
What a shame.  I went thru the normal package upgrade process today that was recommended under the adept updater and now my camera won't work again.   And I know it was something in the upgrade as I used it just yesterday and uploaded some photos just fine.  Now ... it recognizes my camera, a Kodak Easyshare CD33 but under gthumb I get the following error when trying to import photos (though it does show my camera model as recognized):

*An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x40a, product 0x59c). Make sure this device is connected to the computer.*

That's what I get with gThumb thought my Kodak is listed right above the error.

With DigiKam, it just says:

*Failed to connect to camera. Please make sure its connected properly and turned on. Would you like to try again?*

The camera is on and detected by my system but no ability to import.

This sux.  It seems that every other time I do the recommended package upgrades, something breaks on my system.

Also of note ... the above solution I tried before, I tried again but to no avail this time. My camera is actually still correctly identified on rules file that I updated successfully on the previous problem.  I went thru the steps again just in case ... but nothing.   I need help.

---

### Post by FM1 on 2007-03-11
FWIW, I got the "Could not claim the USB device..." import error last night, though my Canon S3 IS had always worked fine, right up to the latest update. Adding a line with the device IDs from lsusb didn't do anything because the line was already there. I came across the bug report linked below and tried changing BUS!="usb*" to SUBSYSTEM!="usb_device" in my 45-libgphoto2.rules. Restarted udev and now it works again.

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")

---

### Post by fiatguy85 on 2007-03-11
> **FM1 said:**
> FWIW, I got the "Could not claim the USB device..." import error last night, though my Canon S3 IS had always worked fine, right up to the latest update. Adding a line with the device IDs from lsusb didn't do anything because the line was already there. I came across the bug report linked below and tried changing BUS!="usb*" to SUBSYSTEM!="usb_device" in my 45-libgphoto2.rules. Restarted udev and now it works again.

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")

Thanks, I have been trying to figure this out.  My Canon Digital Rebel XT / 350D worked yesterday, but then I updated and it would not connect.  Changing that line fixed it.

---

### Post by myke on 2007-03-11
> **FM1 said:**
> FWIW, I got the "Could not claim the USB device..." import error last night, though my Canon S3 IS had always worked fine, right up to the latest update. Adding a line with the device IDs from lsusb didn't do anything because the line was already there. I came across the bug report linked below and tried changing BUS!="usb*" to SUBSYSTEM!="usb_device" in my 45-libgphoto2.rules. Restarted udev and now it works again.

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")


Thanks ... that solution worked perfectly for me as well.  How did you figure out how to change that one little part of the 45-libgphoto2.rules file?   It worked great but I never would have known enough to know to change that.   I don't know how it worked but it did which is great.

---

### Post by netterfield on 2007-06-16
The above changes worked for me with Edgy and a Kodak C875.

But: don't forget to unplug the camera before you restart udev.  If you leave it on and plugged in, it will sit there and keep not working until you do...

---

### Post by djaart on 2007-08-09
Yeah the "SUBSYSTEM" fix worked for me also with a cx6200 from kodak. that was also in the list already....
thanks!

---

### Post by helpdeskdan on 2007-12-25
Ditto on Subsystem for a mini Vivitar Digital Camera - many thanks!  (Cd302n)

---

