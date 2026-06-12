---
title: "Gutsy + iSight: works but something very weird"
date: 2007-11-01
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-11-01
I'm using a MacBook (C2D) to run Ubuntu Gutsy, openSUSE 10.3 and Sidux 2007-3 as well as OSX (tiger).
I managed to get the iSight webcam working in openSUSE and Gutsy (only tested it in Kopete) where it works fine .........up to a point.
Apparently, however, if I shutdown the computer for a while (e.g. overnight), Kopete no longer detects any webcam device in either Gutsy or SUSE when the computer is switched on again.
I have tried re-installing the "dependencies" for iSight as well as the uvcvideo driver (SUSE only, I have not installed any driver in Gutsy) but all to no avail.
However, if I boot to OSX and activate iSight in iChat and then go back to either Ubuntu or SUSE, iSight is once more detected and fully operational in Kopete.
I have seen this over the last three days so it's not a one-off. However, it beats me to explain how what I do in OSX should influence the operability of hardware in Ubuntu and SUSE.
Anybody know what's going on here?

---

### Post by cyberdork33 on 2007-11-01
I would guess that there is some initialization that Ubutnu is not doing correctly.

I was having a strange problem in feisty with the iSight at one time where everything was very dark in Ubuntu, but worked fine in OSX. I found that a few other people were having odd issues with this too, and resetting the SMC seemed to fix it. I suggest trying that as it will not really change anything on the system, and it pretty easy to do:
[http://docs.info.apple.com/article.html?artnum=303319](http://docs.info.apple.com/article.html?artnum=303319)

So is your iSight working at full resolution? 640x480 ?

---

### Post by PaulFXH on 2007-11-01
Thanks for the reply.
I'll try that SMC reset thing tonight as the problem only seems to occur after the machine has been shutdown for quite some time. Shutting it down for an hour or so doesn't seem to affect the operability of iSight (in Kopete) in either Gutsy or openSUSE.
> So is your iSight working at full resolution? 640x480 ?
Unfortunately, I have no idea what the image resolution is. The Kopete Settings>Configure box provides neither information nor control on the resolution. If you could perhaps let me know how to check this, I will do so.

I'm also puzzled as to why I didn't have to install any webcam driver in Gutsy to get iSight to work. In openSUSE, the uvcvideo drivers are installed with the basic setup but Synaptic (in Gutsy) shows no signs of any installed webcam drivers on my MacBook.

---

### Post by cyberdork33 on 2007-11-01
> **PaulFXH said:**
> Thanks for the reply.
I'll try that SMC reset thing tonight as the problem only seems to occur after the machine has been shutdown for quite some time. Shutting it down for an hour or so doesn't seem to affect the operability of iSight (in Kopete) in either Gutsy or openSUSE.

Unfortunately, I have no idea what the image resolution is. The Kopete Settings>Configure box provides neither information nor control on the resolution. If you could perhaps let me know how to check this, I will do so.

I'm also puzzled as to why I didn't have to install any webcam driver in Gutsy to get iSight to work. In openSUSE, the uvcvideo drivers are installed with the basic setup but Synaptic (in Gutsy) shows no signs of any installed webcam drivers on my MacBook.

The changes were made to the gutsy kernel module code to support iSight by default. There is a bug in gstreamer though that prevents the camera from working at the resolution it is detected to work at (and is supposed to work at). 

Try this command to test the iSight through gstreamer @ 640x480:
```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
```
Try this command to test the iSight through gstreamer @ 352x288 (should work):
```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
```
This problem is why iSight is not working with cheese and other apps at the moment.

---

### Post by PaulFXH on 2007-11-01
OK, I first tried the command for the 352x288 resolution and I got this output in the terminal:
```
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /pipeline0/ximagesink0: Output window was closed
Additional debug info:
ximagesink.c(1061): gst_ximagesink_handle_xevents (): /pipeline0/ximagesink0
Execution ended after 21235472000 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
FREEING pipeline ...

```
and a small video window opened up which was basically the same size as I get in Kopete.
When I tried the 640x480 command, however, I get this in the terminal:
```
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock

```
and that's it. Nothing else happens and no webcam window opens.
Not only that but when I checked the webcam image in Kopete after this, only a frozen image was displayed (like a snapshot).

---

### Post by cyberdork33 on 2007-11-01
> **PaulFXH said:**
> OK, I first tried the command for the 352x288 resolution and I got this output in the terminal:
```
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /pipeline0/ximagesink0: Output window was closed
Additional debug info:
ximagesink.c(1061): gst_ximagesink_handle_xevents (): /pipeline0/ximagesink0
Execution ended after 21235472000 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
FREEING pipeline ...

```and a small video window opened up which was basically the same size as I get in Kopete.
When I tried the 640x480 command, however, I get this in the terminal:
```
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock

```and that's it. Nothing else happens and no webcam window opens.
Not only that but when I checked the webcam image in Kopete after this, only a frozen image was displayed (like a snapshot).

Yea that sounds like what I have been getting. still waiting for something to happen on this bug. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638)
[https://bugs.launchpad.net/ubuntu/+bug/131222](https://bugs.launchpad.net/ubuntu/+bug/131222)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/127584](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/127584)

---

### Post by PaulFXH on 2007-11-01
OK, thanks.
Just for completeness, I should mention that I didn't use your [guide]("http://ubuntuforums.org/showthread.php?t=491381") to get iSight working in Gutsy (didn't see it until today) as I basically just adapted a method that had worked well for me in openSUSE 10.3. This is it [here]("http://wiki.suselinuxsupport.de/wikka.php?wakka=HowToSetupalogitechUsbWebcam").
However, the versions of the "dependencies" I installed were sometimes different from what's mentioned in this latter guide.
Here's what I installed (or in some cases were already installed in Gutsy).

xawtv  3.95.dfsg1-ubuntu
pia       3.95.dfsg1-ubuntu
tv-fonts  1.1-4
libraw1394-8  1.2.1-3build1
libavc1394-0  0.5.3-1build1
libdv4  1.0.0-1ubuntu1
libquicktime1  2.1.0.0+debian-4ubuntu1

The other three "dependencies" mentioned in the guide I used were just ignored largely because I couldn't find them. 
After this, iSight worked fine in Kopete other than the fact that I need to activate iSight in OSX now and again to make sure it keeps working in Ubuntu and SUSE.

---

### Post by cyberdork33 on 2007-11-01
> **PaulFXH said:**
> OK, thanks.
Just for completeness, I should mention that I didn't use your [guide]("http://ubuntuforums.org/showthread.php?t=491381") to get iSight working in Gutsy (didn't see it until today) as I basically just adapted a method that had worked well for me in openSUSE 10.3. This is it [here]("http://wiki.suselinuxsupport.de/wikka.php?wakka=HowToSetupalogitechUsbWebcam").
However, the versions of the "dependencies" I installed were sometimes different from what's mentioned in this latter guide.
Here's what I installed (or in some cases were already installed in Gutsy).

xawtv  3.95.dfsg1-ubuntu
pia       3.95.dfsg1-ubuntu
tv-fonts  1.1-4
libraw1394-8  1.2.1-3build1
libavc1394-0  0.5.3-1build1
libdv4  1.0.0-1ubuntu1
libquicktime1  2.1.0.0+debian-4ubuntu1

The other three "dependencies" mentioned in the guide I used were just ignored largely because I couldn't find them. 
After this, iSight worked fine in Kopete other than the fact that I need to activate iSight in OSX now and again to make sure it keeps working in Ubuntu and SUSE.those may be needed to activate it within kopete, but as far as I know, there are no 'dependencies' required to get it working (technically) within Ubuntu.

That's ok that you didn't use that guide as I pretty sure it isn't needed anyway (anymore).

---

