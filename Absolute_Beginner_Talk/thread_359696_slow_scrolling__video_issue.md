---
title: "slow scrolling / video issue"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by tommyp on 2007-02-12
I just set up a new computer using this motherboard (recommended in the compatibility guide):

[http://www.biostar-usa.com/mbdetails.asp?model=geforce+6100-m9](http://www.biostar-usa.com/mbdetails.asp?model=geforce+6100-m9)

I am using the onboard video, but there is a very noticeable delay (like a flicker) when using the scroll wheel. It's as though the whole page reloads rather than moving smoothly down.

Is this a driver problem?  I tried to load the latest nvidia drivers from tseliot's pages, but it screwed up my xorg files.  Should I be using the legacy driver?

Is it a screen resolution / refresh problem?  My monitor is making a slight high pitch whine.  When I try to change the screen resolution under the system preferences menu, the screen changes, freezes, then goes back to the sign in screen at the original resolution.

Thanks for your help!

---

### Post by shanepardue on 2007-02-12
It definitely sounds like a driver issue. You don't need the legacy driver because that's a newer video card. When you installed the latest nvidia driver, did you use envy? That is available on his website and works like a charm. Or, you can do it manually as guided in the wiki.. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by r4ik on 2007-02-12
Envy,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by tommyp on 2007-02-12
Thanks.  I'll try envy tonight.

Any idea why the screen would freeze and kick me out after attempting to change the resolution?

---

### Post by r4ik on 2007-02-12
I think it is driver related.

---

### Post by tommyp on 2007-02-14
The default driver was incorrect and Envy was the solution.  It worked great!!!  

Many thanks to all those who helped and especially to Alberto for creating it!

---

### Post by Wizzy on 2007-02-14
I've got the exact same problem, except with a Sapphire Radeon x1800xt

I just installed Ubuntu. So I haven't touched anything at all - I'm curious if anyone has a suggestions. I'm quite new to Linux.

---

### Post by shanepardue on 2007-02-14
Read this thread from the beginning. Envy works for ATI also.

---

