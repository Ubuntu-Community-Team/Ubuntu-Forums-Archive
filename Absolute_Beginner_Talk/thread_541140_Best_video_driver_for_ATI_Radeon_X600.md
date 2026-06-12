---
title: "Best video driver for ATI Radeon X600"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by bootsbradford on 2007-09-02
Sorry for the obvious question but the more I read about this the more confused I get. If someone could just spell it out for me simply that would be great!

I have an ATI Radeon X600 video card. Using the open source driver has resulted in lots of freezes ever since the move to Feisty. I have moved to the proprietary one via the restricted drivers manager and so far, so good - no crashes.

I have also seen discussion [here]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") about the 8.40.4 driver. 

What is the difference between all the drivers? Which one am I best to use?

---

### Post by mali2297 on 2007-09-02
I have an ATI Radeon Mobility X700 card and use the open source *radeon* driver, mainly since I wanted to enable Beryl with AIGLX. The *fglrx* seems to me to be more stable and as long as you don't want AIGLX, I would suggest you stay with that which works best.

---

### Post by bootsbradford on 2007-09-02
So is it not possible to do Beryl/Compiz with the fglrx driver?

I did love Compiz while on the open source driver, but can't justify 2-3 crashes a day for the sake of a few fancy effects!

---

### Post by mali2297 on 2007-09-02
> **bootsbradford said:**
> So is it not possible to do Beryl/Compiz with the fglrx driver?

It should be possible with the use of XGL in place of AIGLX, but I haven't manage to get that working.

> I did love Compiz while on the open source driver, but can't justify 2-3 crashes a day for the sake of a few fancy effects!

Are you're sure it isn't Compiz that is causing the problems rather than the driver? I experience crashes when running the latest Compiz Fusion but when I turn back to the standard window manager I'm fine (except for an unreadable screen when switching to tty[1-6] or logging off).

---

### Post by bootsbradford on 2007-09-07
I've just run the command 'flgrxinfo' just out of curiosity. I'd expected to find something about an ATI driver given that was what I thought I'd installed in the Restricted Drivers Manager.

Instead I was given this output:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Is this the best thing for me to be running on an ATI Radeon X600 card?
If not what do I need to change to, and how?

Thanks.

---

### Post by bootsbradford on 2007-09-08
Really hoping someone can help me with this...

With an ATI Radeon X600, and using the Restricted Drivers Manager, should I have an ATI proprietary driver?

If so, can anyone explain why my flgrxinfo output is as follows:

Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Thanks.

---

### Post by mali2297 on 2007-09-08
You mainly have to choose between the open source 'radeon' and the proprietary 'fglrx' driver:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
The links might give you some clues to your questions.

---

