---
title: "Mac Mini 7.04 Hardware Support"
date: 2007-12-04
forum: Apple Intel Users
---

### Post by AriXmail on 2007-12-04
Hey everyone,

I recently bought a Mac Mini to be used as a Backend, Frontend, Regular Desktop setup in MythTV. I'm outputting with DVI to DVI, but I hear that's buggy in 7.10, so I'm going with 7.04 for now (I even tried with 7.10, and it was stuck at 640x480, and when I mucked with my xorg.conf it got totally messed up).

So, my main question is, will Audio Out (I'm using minijack for now) work fine? Is there anything I will need to do to get it working?

Is there anything else I should know about 7.04 on the Mac Mini? And, should I install the i810 modesetting driver?

Thanks! :)

---

### Post by cyberdork33 on 2007-12-04
> **AriXmail said:**
> Hey everyone,

I recently bought a Mac Mini to be used as a Backend, Frontend, Regular Desktop setup in MythTV. I'm outputting with DVI to DVI, but I hear that's buggy in 7.10, so I'm going with 7.04 for now (I even tried with 7.10, and it was stuck at 640x480, and when I mucked with my xorg.conf it got totally messed up).

So, my main question is, will Audio Out (I'm using minijack for now) work fine? Is there anything I will need to do to get it working?

Is there anything else I should know about 7.04 on the Mac Mini? And, should I install the i810 modesetting driver?

Thanks! :)

No, use the 'Intel' driver

---

### Post by AriXmail on 2007-12-04
> **cyberdork33 said:**
> No, use the 'Intel' driver

Thanks for the response. When using the intel driver, do I have to do the LinearAlloc thing for HD? Sorry for so many questions :P

Thanks again!

---

### Post by cyberdork33 on 2007-12-04
> **AriXmail said:**
> Thanks for the response. When using the intel driver, do I have to do the LinearAlloc thing for HD? Sorry for so many questions :P

Thanks again!
I don't even know what that is... The Intel driver surpased the i810 driver awhile ago though as the recommended driver to use.

---

### Post by AriXmail on 2007-12-04
> **cyberdork33 said:**
> I don't even know what that is... The Intel driver surpased the i810 driver awhile ago though as the recommended driver to use.

Hmm, OK. What about the audio drivers?

---

### Post by AriXmail on 2007-12-04
Grr. I installed the xserver-xorg-video-intel (which I assume fixes the xorg.conf to use the intel driver? If not, no wonder because xserver-xorg-video-intel uninstalls i810) onto 7.04, and after restarting X, I get a blank screen. Same thing happens when I use the intel driver on 7.10 (except it's already installed to 7.10). On 7.10, however, only vesa works (640x480), and i810 has the same problem as the intel driver :/

I'm using DVI to DVI.

---

### Post by cyberdork33 on 2007-12-05
> **AriXmail said:**
> Grr. I installed the xserver-xorg-video-intel (which I assume fixes the xorg.conf to use the intel driver? If not, no wonder because xserver-xorg-video-intel uninstalls i810) onto 7.04, and after restarting X, I get a blank screen. Same thing happens when I use the intel driver on 7.10 (except it's already installed to 7.10). On 7.10, however, only vesa works (640x480), and i810 has the same problem as the intel driver :/

I'm using DVI to DVI.
you shouldn't need to install anything... just make sure that the Driver line in your xorg.conf specifies Intel .

---

### Post by AriXmail on 2007-12-05
> **cyberdork33 said:**
> you shouldn't need to install anything... just make sure that the Driver line in your xorg.conf specifies Intel .

7.04 doesn't come with the driver intel, and once I install it, it doesn't work. 7.10 does come with the driver intel, and once I use it in my xorg.conf, it doesn't work either. What am I doing wrong??

---

