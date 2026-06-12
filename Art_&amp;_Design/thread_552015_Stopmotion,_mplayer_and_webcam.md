---
title: "Stopmotion, mplayer and webcam"
date: 2007-09-15
forum: Art &amp; Design
---

### Post by Keyper7 on 2007-09-15
Hi guys,

I need some help with my Ubuntu 7.04 64-bit in a HP Pavilion dv6258se laptop.
I'm using the integrated webcam with Sam Revich's r5u870 driver and svn mplayer.

My problem is with stopmotion. If I try to start it, it immediately segfaults and gives

```

ioctl: VIDIOCGFBUF(base=(nil);height=0;width=0;depth=0;bytesperline=0): Invalid argument

```

When I saw that error, I remembered that whenever I type mplayer tv:// I get

```

v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument

```

But the camera image shows up perfectly. Are these errors somehow related?

By the way, I don't remember having those errors in mplayer in the 32-bit version.

Can someone help me? :)

Thanks in advance,
-Keyper7

---

