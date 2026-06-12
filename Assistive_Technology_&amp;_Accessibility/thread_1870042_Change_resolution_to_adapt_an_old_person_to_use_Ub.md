---
title: "Change resolution to adapt an old person to use Ubuntu"
date: 2011-10-26
forum: Assistive Technology &amp; Accessibility
---

### Post by Sircoelho on 2011-10-26
Hi there, people! Everything fine?

My story is about my mother, 67 years old, who want to use Ubuntu to execute daily tasks. (Web, e-mail, word processing, printing). 

The problem is their vision, she has Astigmatism and can't see and understand the icons and text on their Philips 17" 190VW with 1440x900 native resolution. 

I need that my monitor and my NVIDIA card with proprietary (or opened) drivers set the 1280x800 resolution for her cause this is only way she can see and understand what's on the screen.

I have take a look at some workrounds but they look too complicated. Is there an easy way to achieve this?

I know every LCD should work at native resolution, but we have a special case here, an old person with compromissed vision who need see things big in the screen. 

Thank you all in advance, and sorry for bad english. 

Mateus from Brazil

---

### Post by papibe on 2011-10-26
Try opening the 'Nvidia X Server Settings' as root. Open a terminal a run this:
```
gksudo nvidia-settings
```
Then on the left click on 'X Server Display Configuration'. Now on the right adjust the resolution until you're satisfied. When ready click below on 'Save to X Configuration File'.

That's it. Restart your machine to test the configuration.

I hope this helps. Let us know how it goes.
Regards.

---

