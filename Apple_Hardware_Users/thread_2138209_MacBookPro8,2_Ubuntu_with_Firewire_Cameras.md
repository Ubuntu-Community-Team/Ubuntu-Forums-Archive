---
title: "MacBookPro8,2 Ubuntu with Firewire Cameras"
date: 2013-04-23
forum: Apple Hardware Users
---

### Post by Yeraze on 2013-04-23
I've successfully installed Ubuntu 12.10 on my MacbookPro8,2, and applied all the necessary updates.  I'm trying to get it talking to a set of Unibrain Fire-I cameras connected via FireWire to the Macbook tho.  This setup works fine on a similar Ubuntu12.10 desktop I use at my office, but for portability I really wanted it working on my laptop as well.  Currently, when I connect the cameras I see lots of entries in dmesg that firewire devices were detected, and entries appear in /dev (/dev/fw1, etc) but nothing seems to recognize it as a Video source.  I've loaded raw1394, dc1394, ieee1394, avc1394, and every other 1394 apt I could find, but currently the only working video source I have (as far as OpenCV and VLC detect) is my iSight at v4l2:///dev/video0 .

Has anyone had any success with this?  Seems I'm almost there given that it recognizes a firewire _something_ was connected.

---

### Post by Yeraze on 2013-04-23
Ah, I found the issue. By recompiling OpenCV with WITH_1394 ON but with WITH_V4L set to OFF.  Now it works!

Thanks to a friend recommending coriander which pointed out that the camera was actually working.

---

### Post by benjaminabruzzo on 2013-04-30
> **Yeraze said:**
> Ah, I found the issue. By recompiling OpenCV with WITH_1394 ON but with WITH_V4L set to OFF.  Now it works!

Thanks to a friend recommending coriander which pointed out that the camera was actually working.

I am running 12.04 on a Macbook 9,2 (13" non-retina pro).

I am just short of your last stage.  I have coriander installed, and have been trying to get it to see my built in isight.  I had it functional (a year ago) on my macbook air running 10.04, but now coriander can't find the camera on the bus.  Using gstreamer-properties and v4l2, the facetime hd camera will function just fine (v4l2src device="/dev/video0").

I plan on using the camera with ROS ([http://ros.org/wiki/fuerte](http://ros.org/wiki/fuerte)).

Any suggestions?

---

