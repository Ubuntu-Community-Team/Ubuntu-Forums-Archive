---
title: "New to Ubuntu, iSight camera doesn't work on MacBook Pro"
date: 2011-06-13
forum: Apple Hardware Users
---

### Post by Aniro on 2011-06-13
Hi, I'm new to Ubuntu, have been using 11.04 for a couple of weeks on my 13-inch MacBook Pro 5'5 (Mid-'09). I have an issue with the iSight camera not working on Skype. I've checked cheese as well, and I've even purged-removed and reinstalled isight-firmware-tools, yet that hasn't helped. I'm looking for solutions, and I hope that my noobness doesn't offend anyone here in the forums.

---

### Post by FormatSeize on 2011-06-14
You may have to install the drivers for the device. I can only give very approximate directions, as I don't recall the interface of 11.04:
 
Go to System -> Administration -> Proprietary Drivers (or it may say Devices or Hardware, it varies depending on the distro). Your device should show up there. Then choose the option to use that device. Finally, reboot.

---

### Post by Aniro on 2011-06-14
No dice. The only drivers it shows are the Broadcom wireless and the NVIDIA graphics drivers, and both of them are already installed.

---

### Post by CoreyB. on 2011-06-17
> **Aniro said:**
> I have an issue with the iSight camera not working on Skype.

Does it work with Cheese?

According to [the Ubuntu community wiki]("https://help.ubuntu.com/community/MacBookPro5-5/Natty"), iSight is supposed to work out of the box for the MBP 5,5 on 11.04.

---

### Post by Aniro on 2011-06-17
> **CoreyB. said:**
> Does it work with Cheese?

According to [the Ubuntu community wiki]("https://help.ubuntu.com/community/MacBookPro5-5/Natty"), iSight is supposed to work out of the box for the MBP 5,5 on 11.04.

Nope, not working with Cheese either.

---

### Post by tucun on 2011-07-04
Hi, 

I am having the same problem with built-in iSight on a MacBook Pro 5,1.
I just made a fresh install of Ubuntu 10.04 LTS.

The mysterious thing to me is that iSight WAS working out of the box when I ran Ubuntu from the Live CD (just before installing it). Running from the Live CD, I opened gstreamer-properties from a terminal, and in the "Video" tab I was able to see iSight in the drop-down menu and successfully test it with the "Test" button.

Now that I've made the install on the hard drive, I repeat the exact same operation: I open gstreamer-properties, I can still see iSight listed under "Devices" in the Video tab, BUT... when I hit the test button I get the following error message:

libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]

If it was working with the Live CD, I'm guessing there must be a way to get it back to work WITHOUT going through all the firmware hack described here ([https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)). By the way, I tried all that already in a previous Ubuntu install earlier today and had no luck (that's why I went for a fresh install).

Any help is very much appreciated! Thanks.

---

### Post by tucun on 2011-07-04
OK -- in case this is helpful to others, I found the solution to my case after hours of messing around... the culprit was the NVIDIA driver, at least on my MacBook Pro 5,1 running Ubuntu 10.04.

After activating this driver, I noticed that my /dev/video0 simply disappearead. I then went back and completely removed it. Not only I got /dev/video0 back, but now my iSight came back to life as well.

How I did it: 
- Go to System > Administration > Hardware Drivers
- Select the NVIDIA driver you may have installed and choose "Remove"
- Shut down the computer. Turn it back on.
- See if it worked: go to a terminal, type gstreamer-properties, go to the Video tab, see if your iSight is listed under "Devices", hit the "Test" button and... you should see your pretty face captured by the webcam!

---

### Post by Old Codger on 2012-02-25
> **tucun said:**
> OK -- in case this is helpful to others, I found the solution to my case after hours of messing around... the culprit was the NVIDIA driver, at least on my MacBook Pro 5,1 running Ubuntu 10.04.

After activating this driver, I noticed that my /dev/video0 simply disappearead. I then went back and completely removed it. Not only I got /dev/video0 back, but now my iSight came back to life as well.

How I did it: 
- Go to System > Administration > Hardware Drivers
- Select the NVIDIA driver you may have installed and choose "Remove"
- Shut down the computer. Turn it back on.
- See if it worked: go to a terminal, type gstreamer-properties, go to the Video tab, see if your iSight is listed under "Devices", hit the "Test" button and... you should see your pretty face captured by the webcam!

My MacBook seems to have lost /dev/video0 as well. How do you activate it?

---

