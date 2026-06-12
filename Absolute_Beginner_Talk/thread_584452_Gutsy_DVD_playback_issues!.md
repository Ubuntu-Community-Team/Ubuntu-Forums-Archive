---
title: "Gutsy DVD playback issues!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by saxonjf on 2007-10-21
All right, I have switched to Gutsy, and have not enabled Compiz.

Wifey tells me that DVD playback is choppy, and so it is.

I do my homework, enable DMA, install the DVD package from Synaptic, and still the problem continues, and even updated the dvdlib32 package., and I don't have any idea.

Can I get some help?  I hate it when wifey switches to windoze

---

### Post by TeaSwigger on 2007-10-21
Unfortunately I'm not an expert in any of the angles, but perhaps I can prompt an idea from some questions:

Does it still give a choppy playback if you "rip" the DVD to the hard drive and play it from the hard drive? Idea being to narrow the possibilities.

Have you confirmed that the ideal video "driver" is installed and in use?

How is the sound? Sound card setup can mess up video performance oddly enough.

What is the video playback app using? Video output module. Have you tried, for example, X11 or OpenGL? Test the options. Is it using the right video device? 

Deinterlace settings? Is any processing enabled (in the playback app) like picture adjustments? That can cause too much processing, resulting in frame dropping etc.

Not sure hdparm 's DMA settings for the optical drives is relevant anymore since the kernal switch (identifiable by finding they're scd or sr rather than hcd in fstab). That should be ok. Good luck, you'll get it. :)

---

