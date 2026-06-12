---
title: "iSight wacky woes with a MPB 5,5 using Oneiric single boot"
date: 2012-05-09
forum: Apple Hardware Users
---

### Post by HansieCK on 2012-05-09
[CENTER][/CENTER]Hi all

I've spent a fair few days over the past couple of years tinkering with my iSight to get it to work. Often it'll stop working after an update (generally a distro upgrade) but I'm usually able to hack away to get it back. Not this time. It stopped working maybe a couple of weeks ago (that I noticed) and I've not been able to fix it to get it to work for Skype, cheese, or gstreamer.

However! It works fine using uvcview - the green light comes on and the picture of me looking dopey appears in the little screen. When I try cheese, I just get a black screen, when I try Skype, the same thing happens in the 'video test', and when I try gstreamer-properties (with 'built-in iSight' as the chosen device), a popup says:

"Video for Linux 2 (v4l2): Error starting streaming on device '/dev/video0'."

and the command line says:

```
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(2143): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]
```

my dmesg from boot shows the following:

```
[   21.018125] uvcvideo: Scanning UVC chain: OT 2 <- PU 3 <- IT 1
[   21.018130] uvcvideo: Found a valid video chain (1 -> 2).
[   21.099845] uvcvideo: UVC device initialized.
[   21.100173] usbcore: registered new interface driver uvcvideo

```

If I do a

```
$ sudo /usr/lib/udev/ift-load --firmware /lib/firmware/isight.fw 
```

I get
 
```
ift-load: USB device 0x05AC:0x8300 not found
ift-load: No iSight found
```


Any ideas? Let me know if you want any more info, too, please!

---

