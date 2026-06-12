---
title: "Need help getting second video card to work"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by jchilton on 2007-10-21
Perhaps my google-fu is weak today, but I've not been able to find a good tutorial anywhere to help me with this. I'm a complete linux newbie, so bear with me if I'm asking a dumb question.

I've just installed Gutsy on my desktop. It works great. However, I've got two video cards. The original is in the AGP slot and is a "nVidia Corporation NV II DDR [GeForce2 MX200]". I upgraded this a while back with an "ATI Technologies Inc RV280 [Radeon 9200 PRO]" in a PCI slot. For WinXP, changing over to this new card was pretty easy: reset the BIOS to send video to PCI instead of AGP, let the hardware manager do its thing, and it worked great.

When I installed Gutsy, I found I had to go back to the AGP nVidia card. So my question is, what exactly do I need to do if I want Gutsy to use my PCI ATI Radeon card? Clearly I need to adjust the BIOS parameters (and move the video cable). I gather there's something I should edit in /etc/X11, but I haven't got anything to work. Can somebody point me toward a tutorial for dumb newbies that explains what I need to do? If it helps, the Radeon card's PCI address appears to be 2:11:0.

And just to be clear...I'm only using one monitor--I'm not trying to set up a dual-monitor output.

---

