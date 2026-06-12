---
title: "Jaunty Xorg won't work on Pismo; tried all suggested fixes"
date: 2009-09-16
forum: Apple Hardware Users
---

### Post by ceratophyllum on 2009-09-16
I switched to Debian 5.0.3 and was able to get Xorg working by specifying Hsync and VertRefresh for pismo's LCD as suggested by others in earlier posts.

I think there is some problem with agpgart or fb. Xorg.0.log has a lot of errors about not being able to open /dev/fbX. No scrambled screen, X just won't start at all. I am totally confused about the modules involved with framebuffer and Xorg direct rendering. (Most of my computers are x86 with fairly generic video that just worked, so I didn't need to learn about DRM and its modules.)

Anyway none of the xorg.conf modifications for the pismo that can easily be found in ubuntu forums worked in jaunty.  Just thought I should mention this in case someone knows how to fix this problem.

What with the declining interest in PPC, I guess I'm not too optimistic.

---

