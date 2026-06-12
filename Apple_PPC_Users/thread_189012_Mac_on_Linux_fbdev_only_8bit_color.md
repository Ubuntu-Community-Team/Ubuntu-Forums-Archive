---
title: "Mac on Linux fbdev only 8bit color"
date: 2006-06-04
forum: Apple PPC Users
---

### Post by yojimbo-San on 2006-06-04
Installed MoL happily (didn't even see [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto) until it was finished!), but I have problems getting a useable colordepth in full-screen/console/framebuffer mode (whatever it should be called)

molvconfig only finds an 8-bit mode, and OSX in 256 colours is ugly :-|

I have an iMac 17" lcd machine, with nVIDIA GeForce4 440 32Mb - Ubuntu is happy at 1440x900 (24bits?) ... 

Any advice on how to improve MoL would be very welcome!

---

### Post by Ptero-4 on 2006-06-05
It seems to be a known bug. Mol can't use colordepths higher than 8bit in those Nvidia GeForce4 cards.

---

### Post by projectle on 2006-06-20
Hmm...

I have a Powerbook G4 17" HR (5,9) and it has the same issue...
Sort of...

At any resolution greater than 800x600, I am limited to 8-bit color.
When I attempt to start at my native 1680x1050, I see nothing.
When I attempt to start at 1440x900, I see everything at 8-bit.

Any ideas?

---

