---
title: "[SOLVED] Webcam Not Working on Acer 5220"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by kolisikepu on 2008-03-31
Hi Community,

I'm using an Acer Extensa 5220 and I am needing help to install my webcam.  I am running Gutsy and so far I've tried Cheese and Camorama Webcam Viewer.

Cheese - It opens, it ponders and then it closes without showing a picture.
Camorama - I get an error window with "Could not connect to video device (/dev/video0).  Please check connection".

Any suggestions as to what is wrong??

I had Hardy installed yesterday and the webcam was working perfect in it.  I thought I'd go back to Gutsy till the stable/actual release comes out next month.

Any help will be awesome!

---

### Post by Jim! on 2008-03-31
Hi - I'm no ace when it comes to installing webcams in Ubuntu, but this might help (It worked for me) I was never able to get my webcam to work until I installed aMSN - In aMSN while talking to a friend I clicked on the "webcam" icon and went through a sort of step by step installation process, My webcam has been working fine since.

---

### Post by Princey on 2008-03-31
What brand/model of webcam do you use? It's wise to list the specifications of your hardware when asking for help.

---

### Post by kolisikepu on 2008-04-01
> **Princey said:**
> What brand/model of webcam do you use? It's wise to list the specifications of your hardware when asking for help.

....hence why I put Acer 5220.

If I must, it's an integrated Webcam on my Acer 5220 Notebook.  Acer Crystal Eye they call the webcam.

---

### Post by kolisikepu on 2008-04-01
Can anyone assist please.... :(

---

### Post by kolisikepu on 2008-04-01
OK... I did read at this thread this and managed to get it working in Ekiga.  But I don't want it to work in Ekiga, I just want it to work in general with Cheese and Camorama.

I did download a zipped file from this thread, but I don't know how to install.  If I can get some help with it, it'll be awesome.

[http://ubuntuforums.org/showthread.php?t=715366](http://ubuntuforums.org/showthread.php?t=715366)

P.S.  This is my output when I run Cheese.

```
kolisikepu@matrix-linuxacer:~/Desktop$ cheese
** Message: Probing the webcam, please ignore the following, not applicabable tries
** Message: Error running pipeline 'v4l2src ! fakesink': Device '/dev/video0' cannot capture at 640x480 [v4l2src_calls.c(990): gst_v4l2src_set_capture (): /pipeline0/v4l2src0:
Call to S_FMT failed for YUYV @ 640x480: Device or resource busy]
** Message: test pipeline for v4l2src failed:
[v4l2src ! fakesink]: Device '/dev/video0' cannot capture at 640x480
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=640,height=480 ! fakesink': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /pipeline1/v4lsrc0:
Error setting the channel/norm settings: Invalid argument]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=640,height=480 ! fakesink]: Could not get/set settings from/on resource.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-yuv,width=640,height=480 ! fakesink': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /pipeline2/v4lsrc1:
Error setting the channel/norm settings: Invalid argument]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-yuv,width=640,height=480 ! fakesink]: Could not get/set settings from/on resource.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=320,height=240 ! fakesink': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /pipeline3/v4lsrc2:
Error setting the channel/norm settings: Invalid argument]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=320,height=240 ! fakesink]: Could not get/set settings from/on resource.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=1280,height=960 ! fakesink': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /pipeline4/v4lsrc3:
Error setting the channel/norm settings: Invalid argument]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=1280,height=960 ! fakesink]: Could not get/set settings from/on resource.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=174,height=144 ! fakesink': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /pipeline5/v4lsrc4:
Error setting the channel/norm settings: Invalid argument]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=174,height=144 ! fakesink]: Could not get/set settings from/on resource.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /pipeline6/v4lsrc5:
Error setting the channel/norm settings: Invalid argument]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink]: Could not get/set settings from/on resource.
** Message: Error running pipeline 'v4lsrc ! fakesink': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /pipeline7/v4lsrc6:
Error setting the channel/norm settings: Invalid argument]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! fakesink]: Could not get/set settings from/on resource.
using source: videotestsrc
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 41 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Ekiga is configured to work with v4l2 if that means anything to anyone.

---

