---
title: "Graphical glitches running Jaunty on MacBookPro1,1 w/ large screen setup"
date: 2009-08-09
forum: Apple Hardware Users
---

### Post by yipdw on 2009-08-09
Hello all, 

I'm running into some graphical glitches with Jaunty on my first-generation MacBook Pro that I'm having trouble tracking down.  Full info is below. 

I'm running a MacBook Pro 1st-gen (so ATI Radeon Mobility X1600 graphics chip) hooked up to an external monitor running at 2560x1600.  I have the laptop's LCD panel enabled, running at 1440x900, and have the two displays linked together in a single screen.  I have attached xdpyinfo output for more information. 

I occasionally get screen glitches that look like distorted parts of the displayed image.  Running OpenGL applications triggers the problem: performing 3D manipulations in Blender, for example, will cause extreme screen glitching to the point of making Blender unusable.  Other OpenGL applications will completely freeze the system; bzflag, for example, does this on my installation. 

This problem does not occur when: 

* I run in mirrored mode (i.e. 1440x900 mirrored on external and internal LCD)
* I run Windows XP or OS X, splitting a single screen across both displays, running at full resolution on both panels (so probably not a hardware issue) 

I've tried to search for evidence of this bug and any possible workarounds in Launchpad, but the words I have at my disposal ("glitches", "radeon", "opengl", "jaunty", "mobility x1600", ...) are so general -- even in combination -- that filtering irrelevant results out is quite difficult. 

Any pointers to further reading, or possible workarounds, would be greatly appreciated. 

Thanks!

---

