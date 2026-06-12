---
title: "Is the Rage 128 realy that bad for Ubuntu??"
date: 2009-02-08
forum: Apple Hardware Users
---

### Post by GavoKaotik on 2009-02-08
Hi, it's me again...

I have a PowerMac G3 B&W with 350Mhz G3, 650MB RAM and ATi Rage 128 with Ubuntu 8.04.1 running.

The first trouble I had with it was with the video resolution, starting with 800x600 after installing and not offering other options, being my monitor of 17" and with a maximum posible resolution of 1280x960 when it had OSX.

Now, after sorting that issue (is set on 1024x768 now, not a complete solution but a solution at least), I found this one:

I installed Blender and Wings3d last week, just for fun. Both of them worked (specially Wings3d) when I had OSX. Now, with Ubuntu, after starting up, both unexpectedly quits. Looking on the messages log, they say something about the r128 driver.

Besides that, there was something that really pissed me off. When I look on the Visual Effects area on the Appearance app, ir always shows up None. When I try to activate, even on Normal, Ubuntu complains that it can't be done.

Apparently is something with my video card, which is old, but I think it can do more, seriously. I'm assuming that my xorg.conf needs more overhaul, but I don't know where to start. Any ideas?

---

### Post by cyberdork33 on 2009-02-09
> **GavoKaotik said:**
> Hi, it's me again...

I have a PowerMac G3 B&W with 350Mhz G3, 650MB RAM and ATi Rage 128 with Ubuntu 8.04.1 running.

The first trouble I had with it was with the video resolution, starting with 800x600 after installing and not offering other options, being my monitor of 17" and with a maximum posible resolution of 1280x960 when it had OSX.

Now, after sorting that issue (is set on 1024x768 now, not a complete solution but a solution at least), I found this one:

I installed Blender and Wings3d last week, just for fun. Both of them worked (specially Wings3d) when I had OSX. Now, with Ubuntu, after starting up, both unexpectedly quits. Looking on the messages log, they say something about the r128 driver.

Besides that, there was something that really pissed me off. When I look on the Visual Effects area on the Appearance app, ir always shows up None. When I try to activate, even on Normal, Ubuntu complains that it can't be done.

Apparently is something with my video card, which is old, but I think it can do more, seriously. I'm assuming that my xorg.conf needs more overhaul, but I don't know where to start. Any ideas?
it sounds like the driver you are using does not support 3d acceleration.

---

### Post by oTZ on 2009-02-10
> **GavoKaotik said:**
> 
Besides that, there was something that really pissed me off. When I look on the Visual Effects area on the Appearance app, ir always shows up None. When I try to activate, even on Normal, Ubuntu complains that it can't be done.

Apparently is something with my video card, which is old, but I think it can do more, seriously. I'm assuming that my xorg.conf needs more overhaul, but I don't know where to start. Any ideas?

Try checking if your system can handle the compiz effects by going to this link [http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

---

