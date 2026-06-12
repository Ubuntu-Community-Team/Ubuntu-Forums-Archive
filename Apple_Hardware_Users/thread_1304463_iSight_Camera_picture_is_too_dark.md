---
title: "iSight Camera picture is too dark"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by tuwe on 2009-10-29
Hi, this is a bump of an [old thread]("http://ubuntuforums.org/showthread.php?t=464031") i found.

The problem is that the picture of an internal isight webcam is too dark compared to the picture i get with OS X. It seems as if OS X applies some kind of filter to the original image, and Ubuntu does not. 

The solution could be: 
[LIST]
[*] Set up isight webcam according to [the wiki page]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight")
[*] Set Default Input to 'Custom' and in the Pipepline box enter the following:
```
v4l2src device="/dev/video0" ! videoscale ! videobalance brightness=x.x contrast=x.x hue=x.x saturation=x.x
``` where x.x are values between -1 and 1 or 0 and 2, respectively. See [here](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-videobalance.html) for details. If you are not affected by the green capture issue, simply omit the videoscale command.
[/LIST]

I'm going to try this as soon as i get home from work, but maybe someone else wants to try it right now :)

---

### Post by tuwe on 2009-10-29
Testing the new settings worked for me. However, gstreamer-properties does not remember custom settings but falls back to the default settings. There is a bug report on launchpad about this, [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/357042](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/357042)

Does anyone know a solution?

---

