---
title: "Teeny Tiny Text in nVidia"
date: 2011-01-10
forum: Apple Hardware Users
---

### Post by teh603 on 2011-01-10
So I installed Kubuntu 10.10 on my mac mini 3,1. Everything worked smoothly until I ran the updater and installed the nVidia drivers (I was using an install DVD I burned back when I was doing the beta test.

Under nVidia, a lot of text like menus and the like is showing up excessively tiny- like half to one third the size its supposed to. I suspect a problem related to my monitor, which is an LCD TV. This happens at all resolutions.

I can scale up the text in workspace appearance, but the amount of space for menus and icons doesn't change one bit and the larger text just gets chopped off.

Anyone had this same problem? I'm really hesitant about going out and connecting a VGA monitor- I don't have an adapter on hand and I'd rather not go explaining to the Apple store that I'm having trouble with it on Linux.

Ironic thing is, text displayed as part of a web page in Firefox shows at the correct resolution.

Edit: I got to looking in the nVidia controls, and it says my resolution is 49x50 DPI. That should be like 96x96 or so. Hm...

Edit again: It looks like I have the un-solvable HDMI text bug. Anyone got suggestions?

---

### Post by teh603 on 2011-01-10
Ok, found out the problem. This should solve the HDMI small-text bug at least in Kubuntu. Go to System Settings -> Application Appearance -> Fonts and set Force Fonts DPI to 96. It'll take a system restart to get this fully fixed, unfortunately.

---

