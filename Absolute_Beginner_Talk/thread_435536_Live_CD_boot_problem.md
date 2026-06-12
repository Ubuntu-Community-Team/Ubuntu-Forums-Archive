---
title: "Live CD boot problem"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Malviolent on 2007-05-07
Hey there, I've installed ubuntu dapper drake and edgy on some of my old systems, but I'm having trouble on my new system.

My new system is a turion ML-37 64 bit 2.0 ghz, 2 gig ram, with dual nvidia geforce go 7900 GS video cards.  I've tried 64 bit dapper (which hangs on the live CD after selecting the first install option), 32 bit edgy (hangs on live CD after first boot option) and 64 bit feisty fawn (which also hangs after the first option is selectied, seems to get a buffer i/o error many times, passes some checks, and hangs after I hear the boot sound with no graphics.  I'm assuming it's my new video hardware, but i'm curious if there are any solutions to my problem?

---

### Post by jargoman on 2007-05-07
usually there is a way to use vesa. It's a video card standard that doesn't need a specific driver. that way all cards that use this standard will be able to display some video just to get up and running. After that you have to install you nvidia proprietary drivers

---

### Post by jargoman on 2007-05-07
if there is no obvious boot option to use vesa then you can add it manually as a boot option. I don't know the specific command though. 

try vesa or VESA

VGA, and TRIDENT also

---

