---
title: "LiveCD - no video after splash (ATI Radeon 9200)"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ChuckC on 2007-03-29
Hi all,

I'm having trouble with the 6.10 LiveCD.  Basically what happens is that the CD boots fine, I see the splash screen and things seem to be working, but then when I get to what I assume should be the desktop, my monitor goes black except for a blue box that says "Invalid Mode".  I hear the Ubuntu startup sound, so that seems to indicate that everything is booting OK otherwise, I just can't see it.

My video card is an ATI Radeon 9200 (not Mobility or Pro or SE or anything else that I know of) and my monitor is a Vizio P50HDTV 50" plasma display (it has a VGA input).  The manual for the display says that the optimal resolution for the VGA input is 1024x768, which is what I use in Windows (1024x768, 32-bit color).  I tried a few different things at bootup.  I tried using the F4 key to specify that resolution/color depth (as well as the lesser color depths available at that resolution) and I tried selecting Safe Display mode - neither of those things solved my "Invalid Mode" problem.  As far as I am aware from flipping through my TV's manual and on-screen menu, there is not a way for me to tell what video mode the TV thinks it is receiving from the VGA input.

My question is, is there anything else I can pass in on the boot parameters line that might cure this issue?  Judging by the fact that I can hear the startup sound, the CD seems to work just fine otherwise.  Obviously, I can't edit xorg.conf or anything like that because I can't see them :D.  So I think boot-time parameters are my only hope here.

---

### Post by compmodder26 on 2007-03-29
I used to have a 9200 and the same thing happened with me.  I used the alternate CD to install ubuntu, then I booted into recovery mode and edited xorg.conf.

---

### Post by ChuckC on 2007-03-29
Thanks for the reply.  I was really hoping to be able to try it out before deciding to install it or not , so I'm still holding out hope that their might be some magic combination of boot params that allows me to use the LiveCD without installing :).

---

