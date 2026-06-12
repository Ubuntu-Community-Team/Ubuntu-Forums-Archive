---
title: "ATI+XGL+Beryl -&gt; XGL absent"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by getut on 2006-11-16
Ok.. After days and days of hacking trying to get proprietary ATI drivers running on my laptops Radeon Mobility X600 with Ubuntu Edgy, I finally got it and have moved on to trying to get Beryl up and running.

In testing (starting Beryl manually with beryl-manager), I don't get the splash screen that the walkthroughs mention, but I do get the red gem on the tray. It is complaining about not being able to find XGL. In the terminal I get the following output:
```
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```

The video card drivers seem right... fglrxinfo's output is:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.6174 (8.31.5)
```

XGL is truly installed and just to be safe I even remove/purged and reinstalled:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Can anyone help me?

---

### Post by jordanmthomas on 2006-11-16
Couple of things:
```
ps -A | grep X
```
should show XGL and not Xorg
also, in /etc/X11/xorg.conf, do you have composite enabled?
If not, add this at the end:
```
Section "Extensions"
    Option "Composite" "true"
EndSection
```

---

### Post by getut on 2006-11-16
> **jordanmthomas said:**
> Couple of things:
should show XGL and not Xorg
also, in /etc/X11/xorg.conf, do you have composite enabled?
If not, add this at the end:


Thanks for the response. I think these are both problems.
First the composite because I had already investigated that one and think it may be major.

If I change nothing in my xorg.conf except to REMOVE the section that disables composite (in other words enabling it), then my ATI drivers don't start and I get no hardware acceleration.

Here is a link that explains the exact issue I am seeing with the proprietary ATI drivers. [http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/](http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/)

It can't be that XGL and ATI are mutually exclusive can it? Other people have the two working together? XGL+Beryly requires 3d Acceleration, but seem to also require composite which disables 3d acceleration in the ATI drivers.

As for the first question you ask, I AM showing xorg. But all the walkthroughs mention doing the test for Beryl-manager before logging in under the newly created XGL option. Am I just doing something wrong there?

Thanks

---

### Post by jordanmthomas on 2006-11-16
Hmmm..I see what you're saying.
They should work together, but I don't have an ATI card, so I can't promise anything.
Does it work if you log in using XGL instead of Xorg?

Someone familiar with ATI cards might need to help you here, as my card always just works and I don't really know what to troubleshoot.

---

