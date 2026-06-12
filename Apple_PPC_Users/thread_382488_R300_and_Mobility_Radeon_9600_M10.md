---
title: "R300 and Mobility Radeon 9600 M10"
date: 2007-03-12
forum: Apple PPC Users
---

### Post by johj on 2007-03-12
Hello,

I'm having issues with getting 3d hardware acceleration to work on my post-February 2005 PowerBook G4.

Even though [glxinfo reports that direct rendering is working]("http://joh.deworks.net/powerbook/files/glxinfo.out"), I only get around [35fps from glxgears]("http://joh.deworks.net/powerbook/files/glxgears.out") and ~0.5fps in games like ppracer and neverball.

I've heard numerous reports that the R300 driver now is stable and provides good 3d acceleration for these cards. Johannes Berg even [reports to have 3d acceleration working]("http://johannes.sipsolutions.com/PowerBook") on his **identical** PowerBook. So my question is this: is the (latest?) R300 driver included in Edgy? My [Xorg.0.log]("http://joh.deworks.net/powerbook/files/Xorg.0.log") seems to suggest otherwise:

```
(WW) RADEON(0): Enabling DRM support

	*** Direct rendering support is highly experimental for Radeon 9500
	*** and newer cards. The 3d mesa driver is not provided in this tree.
	*** A very experimental (and incomplete) version is available from Mesa CVS.
	*** Additional information can be found on http://r300.sourceforge.net
	*** This message has been last modified on 2005-08-07.
```

Also, [here's my xorg.conf]("http://joh.deworks.net/powerbook/files/xorg.conf").

So, has ynyone gotten 3d hardware acceleration working on a similar card/computer?

Any help and/or pointers appreciated,

---

### Post by ssam on 2007-03-12
could it be the same issue as [https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/56692](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/56692)

---

### Post by johj on 2007-03-12
> **ssam said:**
> could it be the same issue as [https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/56692](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/56692)

Looks strikingly similar, yes. I added my comment to the bug...

---

### Post by johj on 2007-03-13
Tested this on Feisty now and it seems the problem is gone :) I have great working 3d acceleration now!

---

