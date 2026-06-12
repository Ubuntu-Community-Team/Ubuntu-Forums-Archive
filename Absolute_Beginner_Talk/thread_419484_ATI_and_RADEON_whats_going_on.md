---
title: "ATI and RADEON? whats going on?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by reality_hunter on 2007-04-23
Hi, please explain whats going on???

I upgraded to Feisty 7.04 few days ago and this might not have anything to do with that, anyways

On the computer there is an on-board video card
ATI RADEON XPRESS 200 Series [Display adapter]

and since that one didn't support 'full 3d acceleration' I decided to take the video card that was on my old desktop, it was ATI 7000 series.....thats all I could get
and I installed it on my UBUNTU deskbox.....After the reboot found out that I had to reconfigure the 
/etc/X11/xorg.config and I change the ports of the 
"device"     1:5:0    to       1:9:0 and it found that card there.....and I could now log onto the X11

but after about 2 maybe ~5 minutes....the computer would freeze sometimes..........and sometimes the monitor would die (even if the computer is still running)

Then finally, after few hours in vein, i changed the device driver from "ati" to "radeon" in the xorg.config          and it hasn't froze by doing that~!

Do you know what is going on???
I also find that some effects are slowed down a little bit..........but overall I think this should be faster ... because now the onboard video card is not eating my memory, no???


ALSO WHEN I installed edgy I installed it for 
Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
and not for
64bit AMD and Intel computers

I have 2.40 gigahertz AMD Athlon 64............is that the right choice????? or not???



thanks for all your answers

---

### Post by igknighted on 2007-04-23
The ati driver is for certain ATI cards (fireGL and a few others, mostly older I think).  The "radeon" driver is for newer radeon cards (like the x700).  There is also the proprietary fglrx driver that gives better gaming performance, but worse performance for desktop effects and rendering.

As for 64bit vs. 32bit, as a new user 32bit is a little easier, and for most apps makes no difference.  I'd say stick with that for now.

---

