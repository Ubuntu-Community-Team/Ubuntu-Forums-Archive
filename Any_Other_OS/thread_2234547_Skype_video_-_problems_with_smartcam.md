---
title: "Skype video - problems with smartcam"
date: 2014-07-15
forum: Any Other OS
---

### Post by itias on 2014-07-15
After couple of days of trying to troubleshoot and googling I finally gave up and thought I would ask question here.
So here is the problem: I tried to revive my old T42 laptop which was used by my kids for chess training. I had a cheap webcam that worked under XP but now with support ceased, I decided to go linux. I installed Linux Mint 13 XLDE, because that was the last one supporting non-PAE processor out of the box. Unfortunately my webcam was not supported so I tried to find another cheap solution and I used smartcam software ([http://sourceforge.net/projects/smartcam/](http://sourceforge.net/projects/smartcam/)) with my old Nokia E52 phone. I compiled the driver (after some trial-err-patch cycles) and I finally had video working in the smartcam app. Also *gstreamer-properties* shows displays video correctly when testing the Default Input.
Unfortunately Skype (v4.2.0.11) shows black box in video options.
I tried LD_PRELOAD the v4l1compat.so trick but to no avail.
Can anyone shed some light and help me with solving the puzzle?

Thanks

Greg

---

### Post by mörgæs on 2014-08-04
Mint 13 is old software. Better to begin with something recent like Lubuntu 14.04.1.
The [PAE]("https://help.ubuntu.com/community/PAE") problem is easily solved.

---

### Post by coffeecat on 2014-08-04
*Thread moved to **Other Operating Systems and Projects**.*

---

### Post by sarlis on 2015-04-11
Hey guys, 

just download smartcam application from google play store and turn your android phone or tablet into a camera

here is the source code with all patches applied to be compiled in kernel 3.13.0-49


[ATTACH]261232[/ATTACH]

---

### Post by IlyasRK on 2015-12-01
thank you!

---

