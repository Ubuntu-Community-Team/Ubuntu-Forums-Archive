---
title: "Boot to Live CD bugs out, hangs"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Sichae on 2008-01-21
I looked into all of the suggested threads before starting this topic and didn't find a similar problem. If someone could point me in the right direction, I'd be very thankful.

I've been wanting to get into Linux for a long time now and I am finally getting around to it. I downloaded the Live CD and burnt it to a disc, booted from the disc, and when I hit install/start Ubuntu, the orange bar moves back and forth, then the image kinda spazzes out and freezes. Shortly after, a console type deal shows up (blinking underscore), but nothing can be typed in. And it kinda just sits there.

I looked around and found a way to install using Wubi, so I did this and it appeared to have worked fine, except for when I boot. I select Ubuntu from the list of OSs and the load bar appears and starts to move, then stops at 1/3, goes to a text readout. The last legible line reads something along the lines of "User Login" or something, but the screen goes blank shortly thereafter.

Any ideas?

AMD Athlon 64 X2 Dual (1.9 ghz per core)
2 GB RAM
80 GB HDD + 200 GB HDD (if it helps, I have a portable HDD of 120, where I have music and movies backed up to in case of a pineapple situation)
NVIDIA GeForce 7300 GT

---

### Post by Sichae on 2008-01-21
I found a solution to the bugout, but it then pulls a [my other try] route. I pressed F6 at the install screen and typed in "video=vga16:off" which then brought it to the load bar screen and the bar started to load, but when it was done, it went to the console screen (blinking underscore) and things could be typed in, but shortly afterwards it went to black screen.

Edit: I found out the main problem with the Live CD and I got into it, but all I see is the X icon and after I try to configure for my video card and monitor, it jumps back to a screen with four text lines and a blinking underscore. I don't recall the exact lines, but one of them had to do with loading boot scripts from /etc/**.local (** is something I can't recall). They all said [ OK ]. Didn't know what to do afterwards.

---

