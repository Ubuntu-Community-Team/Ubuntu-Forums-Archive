---
title: "iSight Camera + Skype 2.0beta with Video in Ubuntu"
date: 2007-11-09
forum: Apple Intel Users
---

### Post by Zelut on 2007-11-09
So I found yesterday that Skype had released a Linux client with video support, but while my camera will work in Ekiga it will not work in the Skype application.  Now the hard part here is that Skype is non-free so none of us can crack it open to make it work, but I wanted to put the word out there to see if anyone could figure out how to make it work.  It would be nice to be able to use Skype on occasion as SIP is still not terribly widespread.

Any ideas?

[Get Skype Beta with Video for Linux]("http://www.skype.com/go/getskype-linux-beta-ubuntu")

---

### Post by cyberdork33 on 2007-11-09
If it is trying to use the full detected resolution of the iSight, it will not work through gStreamer as there is currently a bug. 

I have no idea how Skype is accessing the camera though as there is poor information on their site.

---

### Post by FunkyM on 2007-11-09
If you upgrade to the [latest uvcvideo driver r141 with the new isight patch applied it will work]("http://i-nz.net/2007/11/04/isight-patch-update-640x480-suspendresume-support/") in ekiga as well as gstreamer applications; this includes the highest resolution and resume/suspend while streaming video.

Skype 2.0's v4l2 interface does not work because it does not support the UYVY format the iSight is streaming (which most other cameras do not use). A bug has been [filed]("https://developer.skype.com/jira/browse/SCL-243").

Thus patience is needed for the Skype guys to add support for it.

---

### Post by cyberdork33 on 2007-11-09
> **FunkyM said:**
> If you upgrade to the [latest uvcvideo driver r141 with the new isight patch applied it will work]("http://i-nz.net/2007/11/04/isight-patch-update-640x480-suspendresume-support/") in ekiga as well as gstreamer applications; this includes the highest resolution and resume/suspend while streaming video.

Good to know.

---

### Post by joselin on 2007-11-09
> **FunkyM said:**
> If you upgrade to the [latest uvcvideo driver r141 with the new isight patch applied it will work]("http://i-nz.net/2007/11/04/isight-patch-update-640x480-suspendresume-support/") in ekiga as well as gstreamer applications; this includes the highest resolution and resume/suspend while streaming video.
 
Skype 2.0's v4l2 interface does not work because it does not support the UYVY format the iSight is streaming (which most other cameras do not use). A bug has been [filed]("https://developer.skype.com/jira/browse/SCL-243").
 
Thus patience is needed for the Skype guys to add support for it.
 
Hope that can be solved soon, will be great if we can use skype on linux.
 
Thanks for the link to the bug. I will follow it.

---

### Post by volanin on 2007-11-10
> **FunkyM said:**
> If you upgrade to the [latest uvcvideo driver r141 with the new isight patch applied it will work]("http://i-nz.net/2007/11/04/isight-patch-update-640x480-suspendresume-support/") in ekiga as well as gstreamer applications; this includes the highest resolution and resume/suspend while streaming video.

I compiled the r140 version downloded from here (All-In-One-Bundle):
[http://i-nz.net/projects/linux-kernel](http://i-nz.net/projects/linux-kernel)

I loaded it fine and then I tested with these commands:
```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
```

The 352x288 mode was ok.
The 640x480 mode still didn't work.
I am doing something wrong here, or the support is still broken?

---

### Post by volanin on 2007-11-10
Nah, forget it!
Everything worked fine after a reboot. Go figure!
:)

---

### Post by Zelut on 2007-11-10
Everything worked fine after a reboot as in video support works for Linux, or just that the higher resolution is supported now?

---

### Post by FunkyM on 2007-11-10
When it "didn't work", you  guys had still used the "old" module, not the new one. You have to run depmod and unload/load the uvcvideo module again to make it work. A reboot fixes this ofc.

---

### Post by cyberdork33 on 2007-11-10
> **FunkyM said:**
> When it "didn't work", you  guys had still used the "old" module, not the new one. You have to run depmod and unload/load the uvcvideo module again to make it work. A reboot fixes this ofc.
gutsy has two versions of he uvcvideo module. One called 'uvcvideo' and one called 'isight_usb'. The isight_usb version is the uvcvideo module that is patched for isight. This is the broken module. you need to load the new uvcvideo module and unload isight_usb. Follow the updated [iSight How To]("http://ubuntuforums.org/showthread.php?p=2957042#post2957042"), and you should be fine.

---

### Post by itsjustarumour on 2007-11-11
> **Zelut said:**
> Now the hard part here is that Skype is non-free so none of us can crack it open to make it work

Hey, don't be too hard on Skype and their dev guys, this is a FIRST BETA after all, not a final product!  That means that LOTS OF THINGS WON'T WORK.  Any first beta is inevitably going to have lots of bugs and Skype 2.0 Beta is no different - thats the whole point.  Just check over on the official dev forum and you'll see there are many issues which are being very actively worked on still.  Just give them time! :-)

---

### Post by cyberdork33 on 2007-11-11
> **itsjustarumour said:**
> Hey, don't be too hard on Skype and their dev guys, this is a FIRST BETA after all, not a final product!  That means that LOTS OF THINGS WON'T WORK.  Any first beta is inevitably going to have lots of bugs and Skype 2.0 Beta is no different - thats the whole point.  Just check over on the official dev forum and you'll see there are many issues which are being very actively worked on still.  Just give them time! :-)
I don't think that is the issue... I think the issue was that it is Non-Free.

---

### Post by itsjustarumour on 2007-11-11
> **cyberdork33 said:**
> I don't think that is the issue... I think the issue was that it is Non-Free.

I think the issue is that he was blaming the bugs in Skype 2.0 Beta on it being non-free, rather than the real reason which is that it is early Beta software.

---

### Post by maluka on 2007-11-11
i've upgraded to the latest driver without any problem. Cheese works :)

when i try to install the skype beta i get this error message:

[IMG]http://i14.tinypic.com/6x9v0nk.png[/IMG]

---

### Post by cyberdork33 on 2007-11-11
> **itsjustarumour said:**
> I think the issue is that he was blaming the bugs in Skype 2.0 Beta on it being non-free, rather than the real reason which is that it is early Beta software.

Exactly. Point being, I could fix it but I can't access the source.

---

### Post by maluka on 2007-11-11
you really realise the limits of closed software when you run into problems with them.

---

### Post by Zaff on 2007-11-12
> **maluka said:**
> i've upgraded to the latest driver without any problem. Cheese works :)

when i try to install the skype beta i get this error message:


You need to remove skype and skype-common and then install the beta package (it worked for me).
```

sudo apt-get remove skype skype-common

```

The beta launches but wen I try the test video thingie I get nothing. the isight is not even on since I don't have the little green light net to it.
I guess I have the same problem as anybody.

---

### Post by cyberdork33 on 2007-11-12
They do not have a 64bit version :(

---

### Post by Zaff on 2007-11-12
> **cyberdork33 said:**
> They do not have a 64bit version :(

can't a 32bit version work under 64 ? I thought you could do that with firefox... (just being curious).

---

### Post by maluka on 2007-11-12
installed the beta successfully but it has no isight support. isight works in amsn, cheese and kopete for yahoo though.

---

### Post by zmjjmz on 2007-11-12
Same here...
It's just a black screen...
At least it detects my iSight...

---

### Post by cyberdork33 on 2007-11-12
> **Zaff said:**
> can't a 32bit version work under 64 ? I thought you could do that with firefox... (just being curious).

Won't install the deb. I could probably get it to run if I extracted the binaries, I just didn't have that much motivation.

---

### Post by Zaff on 2007-11-13
> **cyberdork33 said:**
> Won't install the deb. I could probably get it to run if I extracted the binaries, I just didn't have that much motivation.

How do you do that ? extract the binairies from a deb file I mean. I know this is off topic but I've been confronted to that before (wanted to get inside a deb file without installing it) and I just didn't know how it was possible...

---

### Post by cyberdork33 on 2007-11-13
> **Zaff said:**
> How do you do that ? extract the binairies from a deb file I mean. I know this is off topic but I've been confronted to that before (wanted to get inside a deb file without installing it) and I just didn't know how it was possible...

use dpkg:```
dpkg -x package.deb *destination*
```

---

### Post by benanzo on 2007-12-14
The latest Skype beta has added UYVY color support and I've tested it with the iSight on my first-gen MacBook = Works Perfectly.

[http://www.skype.com/intl/en/download/skype/linux/beta/choose/](http://www.skype.com/intl/en/download/skype/linux/beta/choose/)

```
ben@adola:~$ skype -v
Skype 2.0.0.27
Copyright (c) 2004-2007, Skype Limited
ben@adola:~$

```

Have fun!

---

### Post by pveith on 2007-12-16
Yey, i can even confirm that with ```
dpkg -i --force-architecture skype-debian_2.0.0.27-1_i386.deb
``` it even works on 64-Bit Gutsy.

Now i can Video-Skype on Linux, not bad at all...

---

### Post by cyberdork33 on 2007-12-16
> **pveith said:**
> Yey, i can even confirm that with ```
dpkg -i --force-architecture skype-debian_2.0.0.27-1_i386.deb
``` it even works on 64-Bit Gutsy.

Now i can Video-Skype on Linux, not bad at all...

Awesome I was wondering about that.

---

### Post by Zaff on 2007-12-18
yeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee
works for me too...
Only thing missing now d camorama (i still don't know what it does and i wanna test it). anyone knows if it'll hande the isight soon ? I understand it doesn't support v4l2 yet..

---

### Post by cyberdork33 on 2007-12-18
> **Zaff said:**
> yeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee
works for me too...
Only thing missing now d camorama (i still don't know what it does and i wanna test it). anyone knows if it'll handle the iSight soon ? I understand it doesn't support v4l2 yet..It just looks something like Cheese, but you have some other adjustments for Contrast, Brightness, Hue, etc. I doubt it work work with the iSight very soon as, according to the about page, he wrote this app to learn v4l. There is a new developer working with it now, so maybe there is a better chance.

The only way I could see it working now is if there is some kind of "translation tool" that can emulate a v4l device from a v4l2 device.

---

### Post by dpope on 2007-12-26
I seem to be in the situation everyone else was in a few weeks ago but somehow the issue is not resolved for me.  I'm using 64-bit gutsy on a Rev 2,2 Macbook Pro C2D (Nov 2006) with uvcvideo r158 and skype 2.0.0.27 and when I try to test the video in the Options menu I just get a black screen.  Skype seems to think things are alright because if I double click on it it goes full screen but I still don't see anything.  The driver itself is working though since it works on ekiga, cheese and gstreamer.  Any ideas?

Another annoying but probably unrelated issue is that its hard to get the driver to work after a restart or a suspend.  I am running a custom built 2.6.23 kernel so there's no issue of gutsy's isight_usb module loading but after a reboot or suspend /dev/video0 is no longer there even though the uvcvideo module is loaded.  I then often go back to the original isight_...tar.gz package mentioned elsewhere on this thread and try to run the install script again (which overwrites the firmware) and then after some random fiddling it seems to work again.  Is there a way to get this to work consistently... Is there something I have to do with the firmware or something I should put in a boot script?  I do unload the module on suspend so it might be related to this.

Thanks in advance

---

