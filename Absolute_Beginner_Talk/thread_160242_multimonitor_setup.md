---
title: "multimonitor setup"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2006-04-14
ive been saving up the monitors that i find on the sides of roads around here (cause people are rich, and im cheap, and not yet out of hs).  my video card has an s-video out, dvi out, and vga out. right now i know slightly more than nothing about video cards and monitors.  im working on finding some adapters for the svideo and dvi outs, cause all my monitors are vga.

now the questions:
when i plug in another monitor, will it be automatically recognized? will separate desktops appear on different monitors? this is my goal. is it possible to connect all three monitors, and have then display three different desktops? and finally, are there any good guides for this, if you dont walk to talk me  through this?

im running breezy right now... any more info you need?

---

### Post by stuporglue on 2006-04-14
> now the questions:
when i plug in another monitor, will it be automatically recognized? will separate desktops appear on different monitors? this is my goal. is it possible to connect all three monitors, and have then display three different desktops? and finally, are there any good guides for this, if you dont walk to talk me through this?

It won't auto-detect it, you'll have to edit the config file /etc/X11/xorg.conf

You can either configure it to be mirrored (the same view on all desktops) or extended (one superwide desktop). I'm not aware of it being possible to do different desktops on different screens.

For a guide, sorry I can't help. You may have luck if you google for Xinerama + your video card. Xinerama is the software that lets you have extended desktops.

---

