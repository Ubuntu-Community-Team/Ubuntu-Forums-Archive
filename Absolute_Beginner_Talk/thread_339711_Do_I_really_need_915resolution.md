---
title: "Do I really need 915resolution??"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-01-16
Hi,

I'm running Ubuntu Edgy on a laptop with an Intel 915GM chipset. Obviously when I install Ubuntu the screen resolution is stuck at 1024x768 when my laptop screen is 1280x800. I installed 915resolution but this didn't solve my problem (I've read that on Edgy one should just run sudo aptitude install 915resolution and then restart X). 

However if I manually add the "1280x800" resolution in front all the others in xorg.conf and restart X then the correct screen resolution is displayed! I've done that but I wonder if I should still use 915resolution because this appears to be a deeper mod........or is the manual editing of xorg.conf just exactly the same as running 915resolution????

Should I run a startup script to use 915resolution on Edgy as well??? (I've read this is not required on Edgy...)

Thanks

---

### Post by kilou on 2007-01-16
up

---

### Post by crimesaucer on 2007-01-16
I had the same question a few weeks back. I have the exact size screen as you, and when I checked the display settings, what was listed was Default, and 1064 x 768@60. I am using Default.

Well I wasn't sure if Default supporting my 15.4 inch screen, so I asked and was told that default will handle that size screen resolution and even larger screens.

I also saw on the wiki page that that package (915resolutions) is for if you have a larger (>20") monitor greater than 20 inches.

I could be wrong so keep asking.

---

