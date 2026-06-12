---
title: "Graphics driver problem?"
date: 2009-02-05
forum: Apple Hardware Users
---

### Post by tomtom999 on 2009-02-05
Hi there,

I just tried to use the new "Gnome Do" dock (which looks really cool, btw.).

When I launched id, I became aware that something with my graphics driver is probably not OK, because:

When I put the mouse over the dock icons, the animation effect (the icons are supposed to grow bigger rapidly) took waaaaaaay too long to complete.

I have never installed a graphics driver manually (always let Ubuntu choose the latest that's available). In "Hardware Drivers", the driver "NVIDIA accelerated graphics driver (version 177)" is "Recommended" and "activated and currently in use".

What should I do to correct the problem?

(I have a MacBook Pro 4,1 & Ubuntu 8.10)

Thanks a lot for any help!
Tom

---

### Post by alexmurray on 2009-02-05
This is a known problem with gnome-do and the 177 version of the nvidia drivers - see here for more info: [https://answers.launchpad.net/do/+faq/324](https://answers.launchpad.net/do/+faq/324) 

I would suggest you install nvidia-glx-180 which enables those options by default, then all should be good.

---

### Post by tomtom999 on 2009-02-06
Great, thanks for your help!

I installed the new driver via Synaptic and Gnome Do now rocks!

(No idea why Ubuntu this time didn't suggest the new driver within the automatic update downloading/installing process like it usually does.)

---

