---
title: "firewire webcams?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by PsycoGeek on 2007-10-15
Anyone using a firewire webcam out there?  Do they work on Ubuntu?

---

### Post by steve-shinn on 2007-10-15
> **PsycoGeek said:**
> Anyone using a firewire webcam out there?  Do they work on Ubuntu?

Pleae be more specific, what make & model ??

Thks

---

### Post by PsycoGeek on 2007-10-15
> **steve-shinn said:**
> Pleae be more specific, what make & model ??

Thks

Well, I found [this camera]("http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm"), but my question was general in nature.  I wanted to know if anyone was using ***any*** firewire webcam successfully on Ubuntu.

Also, if you know of any firewire webcams that do work, please list them.  I did look through the hardware compatability list, and a few webcam threads, but saw nothing regarding firewire.

---

### Post by steve-shinn on 2007-10-15
> **PsycoGeek said:**
> Well, I found [this camera]("http://www.unibrain.com/Products/VisionImg/Fire_i_DC.htm"), but my question was general in nature.  I wanted to know if anyone was using ***any*** firewire webcam successfully on Ubuntu.

Also, if you know of any firewire webcams that do work, please list them.  I did look through the hardware compatability list, and a few webcam threads, but saw nothing regarding firewire.


Try this compatability link :-
[http://www.linux1394.org/hcl.php?class_id=3](http://www.linux1394.org/hcl.php?class_id=3)

---

### Post by theJagger on 2008-03-13
> **steve-shinn said:**
> Try this compatability link :-
[http://www.linux1394.org/hcl.php?class_id=3](http://www.linux1394.org/hcl.php?class_id=3)

many of those cameras send DV signals, (mini-DV DV-cam and Digital 8 ). My understanding is that, working with a DV/firewire camera, like most in the list, is a bit different from working with a "webcam" like the iSight, which has a firewire interface but does not send a DV signal.

this page has a section IIDC vs. DV
[http://damien.douxchamps.net/ieee1394/coriander/manual/](http://damien.douxchamps.net/ieee1394/coriander/manual/)

i think typically when the worrd webcam is used it refers to the IIDC type. That same site mentioned above might help get your camera working.

---

### Post by forrestcupp on 2008-03-13
I've used a Sony digital video camera with firewire to capture video in Kino.  It doesn't automatically control my camera through software like certain Windows programs do, but it does work correctly when I set Kino to capture and press the play button on my camera.  So, yes, it's possible.  I didn't even have to go out of my way to make it work.

BTW - Kino is great for capturing, but not so great for editing.

Edit:
Oh, you're talking about 'webcams.'  That's different.  I don't know about that.

---

### Post by emk2203 on 2008-05-11
I have two firewire webcams and played around with them in Ubuntu, and it is safe to say that there is no usable support.

Since there are a couple of misconceptions here in the replies, some explanations:

Do not confuse a firewire webcam with a camcorder. The webcam is a IIDC device, the camcorder is not (it sends compressed data via firewire).

For camcorders, you would use kino and the like (with obviously good support), but for the webcam, you need coriander. While coriander itself is an excellent application for industrial use of IIDC devices, you need more to have a real "webcam" functionality for skype, gnomemeeting etc..

You would need to build the kernel module vloopback (which is no longer maintained) to pipe the coriander output to a v4l device which you could plug into other applications. Frankly, I stopped here.

Even at the risk to annoy a lot of people: Under Windows, you just plug the cameras in, you do not have to install drivers (since at least Windows 2000), you get an icon in your workspace folder where you can see the live image (no further application needed), you can save stills from there and you can use the cams in Skype. We are not talking about installing device-specific software at *any* point.

Now *this* is what I call **supported.**

And if you think I'm frustrated, yes, I am. I would expect linux to do better. The cams are excellent, and I used them for years under Windows, and it's a shame that for linux, you need to go and compile modules etc.

---

