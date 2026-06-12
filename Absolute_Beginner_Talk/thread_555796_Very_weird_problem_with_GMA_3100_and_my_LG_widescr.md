---
title: "Very weird problem with GMA 3100 and my LG widescreen monitor.ç"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by MrGando on 2007-09-20
Hi guys, I am having a very weird problem :( 

I installed the intel driver in this post ( [http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943) ) , that made a difference , because pre-installation I wasn't able to set the monitor to 1440x900 or 1680x1050 in (System - Preferences - Screen Resolution ) , now Screen Resolution lists 1680x1050 as an option. 

The thing is that when I choose 1680x1050, Ubuntu actually goes to it. But my screen does not! , this is VERY weird. My screen is 22 inches LG widescreen, and I use it at 1680x1050 in my MacBook or my windows Machine with this monitor . But in Ubuntu, I change the screen resolution to 1680x1050 , and then I click the "Auto Adjust" button in my screen, the screen blinks and tries to go to 1680x1050. But it cant, I can't even see the Applications and Places menus.

Here is a video that I took of the screen with my nikon camera, it's 10 MB... maybe if you watch it you can understand my problem better.

[http://rapidshare.com/files/57061421/DSCN4578.MOV.html](http://rapidshare.com/files/57061421/DSCN4578.MOV.html)

If you watch the video I change the resolution from 1440x900 to 1680x1050, then I go to the upper left corner of the screen to show you how the System menu looks ( Applications and Places are not visible...  ) then I click the auto adjust button on my monitor , and the video ends, but there are no changes to the problem when I click the button :(

Please I really need help... this is driving me nuts.

---

### Post by MrGando on 2007-09-22
Hi guys I re-installed ubuntu 7.04 desktop i386 on my machine ... I have a Gigabyte motherboard....

This problem is still there, I think I am doing everything fine.


Help anyone ???

---

### Post by MrGando on 2007-10-18
Problem still there .... it got fixed when I installed the nX server ( very weird )....


and now , it just got back when I installed a new hard drive.

---

### Post by thornton on 2007-10-29
I'm Abusolute  Biginner, too. So I'm not sure. I only suggest a probability;

According the brog site, GMA3100's Resolution Capability is limited as follows;
[http://blog.kcg.ne.jp/blog/leeway/1108](http://blog.kcg.ne.jp/blog/leeway/1108)

-600x800
-1024x768
-1252x864
-1280x600
-1280x720
-1280x768
-1280x960
-1280x1024
-1400x1050
-1600x900
-1600x1200
-1856x1392
-1920x1080
-1920x1200
-1920x1440

---

### Post by trappist on 2007-11-14
You need to "downgrade" the driver from "intel" to "i810" in your xorg.conf, and follow some other posts on this site and elsewhere on using the 915resolution tool to hack the appropriate resolution.  Seems to be a problem with Gutsy's version of the intel video drivers.

---

