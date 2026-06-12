---
title: "dual monitors = dual headaches!"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by vitalejd on 2008-01-05
I just got another monitor hooked up to my vid card.  How do I get this monitor to work with ubuntu?  I want to have it like I have my win xp dual monitor set up...one is the primary and the secondary is NOT a clone of the primary monitor.  so basically I can move windows back and forth between the 2 monitors in window$ with the taskbar only on the primary screen.

I tried using the screens and graphics settings in ubuntu and that screwed it up REAL BAD so I had to reconfigure my xserver to get my monitor working again.  So, right now I only have one working monitor with ubuntu.

I have a Samsung 740BX on the digital output and a Samsung 730B (current working ubuntu monitor) on the analog output from my nvidia 7600 GS vid card.  Can anyone help me with this?  Thanks for any help with this!

---

### Post by overdrank on 2008-01-05
> **vitalejd said:**
> I just got another monitor hooked up to my vid card.  How do I get this monitor to work with ubuntu?  I want to have it like I have my win xp dual monitor set up...one is the primary and the secondary is NOT a clone of the primary monitor.  so basically I can move windows back and forth between the 2 monitors in window$ with the taskbar only on the primary screen.

I tried using the screens and graphics settings in ubuntu and that screwed it up REAL BAD so I had to reconfigure my xserver to get my monitor working again.  So, right now I only have one working monitor with ubuntu.

I have a Samsung 740BX on the digital output and a Samsung 730B (current working ubuntu monitor) on the analog output from my nvidia 7600 GS vid card.  Can anyone help me with this?  Thanks for any help with this!

HI and you can try to use nvidia settings with this command ```
gksudo nvidia-settings
``` Then you can setup it up with twinview that will give you the effect as I understand it. Good luck!

---

### Post by vitalejd on 2008-01-05
> **overdrank said:**
> HI and you can try to use nvidia settings with this command ```
gksudo nvidia-settings
``` Then you can setup it up with twinview that will give you the effect as I understand it. Good luck!

Ok, thanks...I'll try it out!

---

### Post by vitalejd on 2008-01-06
> **overdrank said:**
> HI and you can try to use nvidia settings with this command ```
gksudo nvidia-settings
``` Then you can setup it up with twinview that will give you the effect as I understand it. Good luck!

It worked!  Thanks for the help!!

---

