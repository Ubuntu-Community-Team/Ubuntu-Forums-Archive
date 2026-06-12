---
title: "Video4linux and Labtec webcam"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2008-02-18
I have a Labtec webcam, and I'm trying to record. When I use Cheese, I can take photos, but can't record myself.

The error I get with Cheese, is:```
** Message: Probing the webcam, please ignore the following, not applicabable tries
** Message: Error running pipeline 'v4l2src ! fakesink': Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver. [v4l2_calls.c(80): gst_v4l2_get_capabilities (): /pipeline0/v4l2src0:
system error: Invalid argument]
** Message: test pipeline for v4l2src failed:
[v4l2src ! fakesink]: Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver.
using source: v4lsrc ! video/x-raw-rgb,width=640,height=480 ! ffmpegcolorspace

```

So, I guess there's something wrong with Video4linux, but I can't find any info anywhere. 
When I typed lsusb I got this:```
Bus 003 Device 008: ID 046d:08a2 Logitech, Inc. Labtec WebCam Pro

```

I have an Intel integrated graphic card (82801G, ICH7 family says the System > Administration > Hardware panel)


I checked the list: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) and found it there under ID 046d, and it says that I need these drivers: spca5xx/LE gspca v4l1/v4l2. 
But which one of these to choose, and where to find them?

Thanks!:)

---

### Post by ltk5 on 2008-02-18
bump

---

