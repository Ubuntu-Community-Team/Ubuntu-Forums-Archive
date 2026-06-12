---
title: "Installing Driver for WebCam(tar.gz file)"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Douglas Nixon on 2007-11-17
:confused: I have looked at Synaptic but cannot find a Driver for my Creative PD1001 ( an older model) Webcam. I have on my desktop the downloaded   original and the converted  tar.gz file  which I got from a website, but I cannot find out yet where I should go to install this package on Ubuntu (Gutsy Gibbon) . Synaptic does not appear to be any help in this instance. Never done this before-Please NOTE.  Thanks for any help. Douglas Nixon, Cinderford, Glos., U.K.

---

### Post by markharding557 on 2007-11-17
could you explain what you downloaded and what you converted it to

---

### Post by profXavier on 2007-11-17
Post the results from: [FONT="System"]lsusb[/FONT], so we know which camera you have, thus leading us to the correct drivers.

---

### Post by Douglas Nixon on 2007-11-18
MarkHarding 557 and ProfXavier.Thank you both for your replies to my enquiry. I have a CREATIVE Model PD1001 WebCam. I downloaded a ZIPPED file spca5xx  from [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html).   I have BOTH the zipped and the unzipped files on my desktop at the moment,  & as the procedure is not the same as for installing in WinXP., I am NOT sure how to install the driver. Sorry, ProfXavier , being a raw newbie, I am not sure what Isusb means. I am NOT very computer literate. Best Wishes.

---

### Post by markharding557 on 2007-11-18
i have had a look in the file,there is some instructions in the file"install"that you run in a terminal such as make and make and make install.
lsusb is a command that will tell you what is connected to usb.
this link may be of use to you[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by fabiomb on 2007-11-18
Douglas, i have a similar camera and a lot of problems to use it with the drivers in Gutsy Gibbon.

DONT INSTALL THESE DRIVERS

the camera is probably detected but you will not be able to use it with kopete and other appls. I am only capable to use it with ekiga softphone because the camera is detected and used by an v4l2 driver.

what is this?

the older v4l is used by a vast majority of webcam apps, but they are upgrading to v4l2, the problem with spca5xx cameras is that hasn't an official driver, you must to use v4l2.

so, open a terminal an type 

lsusb

the system will give you a list of USB devices, i found in my machine:

Bus 001 Device 004: ID 0c45:602e Microdia

Microdia is the chipset of a spca5xx webcam.

i don't remember all the apps i have installed to get this camera work, but there are many to test it:

if you want to know if your ubuntu is using v4l2 instead of v4l type:

lsmod | grep uvc
or
lsmod | grep video

you will see wich modules are loaded (look to modules as "drivers" in other operating systems)

if you type:

v4lctl -c /dev/video0 list

will tell you a lot of data of the camera and:

v4l-info

too

you can see what is happening in your system with:

dmseg

if you unplug an plug the camera you will see there a lot of info, if you copy all that info we can help you more.

PS: Sorry for my english

---

### Post by Douglas Nixon on 2007-11-18
Hi FABIOMB.  THank you for all the information. I will try all that tomorrow. I have been in here most of the day and I want to spend a little more time with my wife & watch a little Television. Your English language is OK. No problem. Best wishes.:)

---

### Post by Douglas Nixon on 2007-11-19
> **profXavier said:**
> Post the results from: [FONT="System"]lsusb[/FONT], so we know which camera you have, thus leading us to the correct drivers.

I typed Isusb into Terminal and the following was copied :-Bus 001 Device 006 ID 041e:400d Creative Technology Ltd. WEbCam PD1001. TO FABIOMB- The above is the only command in Terminal out of your list that worked- All the others gave the reply "Command NOT found " or "No such file or Directory". Many thanks to all of you for your time . I hope that this information will enable you to help me. Best Wishes.

---

