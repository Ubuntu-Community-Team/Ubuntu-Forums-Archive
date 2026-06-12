---
title: "ppc vs. x86 builds"
date: 2006-06-16
forum: Apple PPC Users
---

### Post by swartzfeger on 2006-06-16
All,

I installed Kubuntu 6.06 on my dual-2.0 G5 at home on a dedicated drive and enjoy using it, so I bought an additional SATA drive for my PC at work and installed 6.06 on my Dell P4 2.8GHz.

The performance disparity is quite noticeable. The PC is extremely quick and smooth, whereas the G5 will often stutter or take a significant amount of time to complete an operation.

For instance -- on the PC, I open System Settings > Appearance, and I can immediately select Fonts, Icons, Style or Window Decorations with no delay. On the G5, I select System Settings > Appearance, and I can't select any of the side options for 5+ seconds.

Also, opening folders/directories in Konqueror is instantaneous on the PC; on the G5, there's a slight delay, almost akin to a quick application launch.

The G5 trounces the PC in every hardware area: dual proc vs. single, 2GB vs 512MB, an ATI 9800 128MB video card vs. a generic Dell OEM video card, faster hard drive, etc.

Is the x86 kernel simply more optimized for its intended platform than the ppc? Could it be my ATI card with less than optimal drivers?

Is there anything I can do on the Mac side to check for bottlenecks/IO issues etc? The only command I really know is 'top', and my CPUs are never pushed. All I've been doing in Kubuntu PPC is playing around, web browsing, playing Kmines, etc. I do eventually want to begin LAMP development, but nothing I've done so far should put any kind of load on my G5.

This will all be moot in a few months when Apple releases pro towers with conroe/woodcrest/x86. :)

---

### Post by AlphaMack on 2006-06-16
PPC isn't as well supported as x86.  There are a lot of tradeoffs such as the lack of codecs, Java, Flash, etc.

I wouldn't necessarily say that x86 is faster than PPC because it depends on the hardware.

There definitely could be an issue with your ATI card and the lack of a well-supported driver (the open source driver isn't all that great).

---

### Post by BoneKracker on 2006-06-20
I suggest you read threads in here that deal with the graphics card you have and optimization of your X configuration.

---

