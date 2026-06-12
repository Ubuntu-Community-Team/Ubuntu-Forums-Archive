---
title: "Debugging kernel panics"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Dylock on 2008-01-25
I've been suffering from kernel panics the last couple weeks. They usually happen when im away at work so I cant say I can link it to any given thing. From what I have been reading people usually get some sort of output when they get a kernel panic.
However for me, i get the locked mouse, locked keyboard, basically a blank screen with my flashing numlock and scroll lock.

How can I start going about tracking this down?
I have already checked syslog.

Thanks :)
Dylock

---

### Post by Dylock on 2008-01-25
Last time this happened i did try the REISUB thing, 
(i help alt + sysrq then typed REISUB)
Since there is no response from keyboard this will not work :/

---

### Post by Dylock on 2008-01-29
Did some looking around on google, apparently the problem I'm having is referred to as a hard kernel panic.

Thanks where the mouse and keyboard are unusable, and the numlock + scrollock are flashing

The only thing that was suggested was to be on console mode and hopefully get the trace dump to that. So when i head to work everyday ill be in console mode hopefully waiting to catch the panic.

---

