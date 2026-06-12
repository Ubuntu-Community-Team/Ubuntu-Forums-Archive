---
title: "iSight not working"
date: 2009-06-01
forum: Apple Hardware Users
---

### Post by spencercarran on 2009-06-01
Macbook 3,1, Ubuntu 9.04 64-bit.

I followed the instructions at [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight) and it sort of works, but there is a green tint on everything as mentioned under gstreamer test. I used the recommended fix to set a "custom" input and put "v4l2src device="/dev/video0" ! videoscale" in pipeline, and this works, but only during the test. As soon as I close gstreamer properties, it reverts back to the previous settings, and even while gstreamer is on, cheese and ekiga give a greenish tint.

---

### Post by tiagobt on 2009-06-01
Yes, this is a known [bug](https://bugs.edge.launchpad.net/mactel-support/+bug/349255). The workaround you mentioned doesn't seem to work every time, and it definitely doesn't work in Skype, aMSN or Cheese. A patch for Cheese is available though. Take a look at the following page:

[https://help.ubuntu.com/community/MacBook2-1/Jaunty#iSight](https://help.ubuntu.com/community/MacBook2-1/Jaunty#iSight)

Tiago

---

### Post by NoBugs! on 2009-06-05
Have you tried installing the [Intrepid webcam driver]("http://packages.ubuntu.com/intrepid/libv4l-0")? The isight worked fine in Intrepid.

```
wget http://mirrors.kernel.org/ubuntu/pool/main/libv/libv4l/libv4l-0_0.5.0-3~intrepid1_i386.deb
sudo dpkg -i ./libv4l-0_0.5.0-3~intrepid1_i386.deb 

```
(if it's 64bit, the "i386" should be changed to "amd64")

---

