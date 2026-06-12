---
title: "[SOLVED] No Sound Plugins!"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by 4l13n666 on 2008-02-29
I just installed new sound drivers and now i have no GStream plugins?

How do i install the GStream plugins? Are there any terminal commands that i can use?

Without these plugins i cannot get any sound at all. This problem appeared after i installed new sound drivers for my HP Pavillion dv6500.

---

### Post by jan quark on 2008-02-29
```
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x libgstreamer0.10-0 libgstreamer-plugins-base0.10-0 python-gst0.10
```


i guess thats the core

---

### Post by 4l13n666 on 2008-02-29
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-esd is already the newest version.
gstreamer0.10-gnomevfs is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-base-apps is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-tools is already the newest version.
gstreamer0.10-x is already the newest version.
libgstreamer0.10-0 is already the newest version.
libgstreamer-plugins-base0.10-0 is already the newest version.
python-gst0.10 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This is all got from using that code! :(

---

