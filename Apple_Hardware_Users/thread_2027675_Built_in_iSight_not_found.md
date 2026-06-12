---
title: "Built in iSight not found"
date: 2012-07-16
forum: Apple Hardware Users
---

### Post by sjared23 on 2012-07-16
Trying to test out my built in iSight webcam on my macbook and it's completely not working.

(gstreamer-properties:5589): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:5589): Gtk-WARNING **: Unknown property: GtkDialog.has-separator gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink' gstreamer-properties-Message: Skipping unavailable plugin 'esdsink' gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink' gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink' gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink' gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc' gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc' gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc' gstreamer-properties-Message: Skipping unavailable plugin 'esdmon' gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc' libv4l2: error setting pixformat: Device or resource busy gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' is busy [gstv4l2object.c(2190): gst_v4l2_object_set_format (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1: Call to S_FMT failed for YV12 @ 640x480: Device or resource busy]

This is what I get. I am able to get the window to come up where I can choose audio and video, but when I go to test, I get nothing. I am completely unsure of what to do.

---

