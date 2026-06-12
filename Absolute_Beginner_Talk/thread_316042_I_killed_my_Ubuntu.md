---
title: "I killed my Ubuntu"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by onemind on 2006-12-10
Hi,

Yesterday I dowloaded the xorg-driver-fglrx  package for my ATI Radeon graphics card onto my ubuntu 6.06 install and it worked fine. However, today i installed the latest version of ubuntu and i downloaded the xorg-driver-fglrx  package again, run this command: sudo dpkg-reconfigure xserver-xorg and went through the steps and made sure to select the fglrx driver. I then restarted the computer, the ubuntu loading screen comes up and then it says ubuntu starting and then my monitor turn off. The screen is blank and it is because i messed with the graphics driver.

Do i have to reinstall ubuntu to get it back because i cant change anything because i cant see the screen.

Any help would be great.

Thanks :)

---

### Post by smile_sunshine on 2006-12-10
Hi,

can you type CTRL+ALT+F1 and get a text screen to log into?

---

### Post by bscbrit on 2006-12-10
Try to start in Recovery Mode to see if you still have access to the command line as root.  If you have, we can go through the process bit by bit until we find what is causing the problem.

---

### Post by onemind on 2006-12-10
Thanks guys,

I pressed ctrl alt f1 and got some text, enetered my username and password and now i have a console.

---

### Post by bscbrit on 2006-12-10
OK, first I would recommend running

sudo dpkg-reconfigure xserver-xorg

again to recover your screen. DO NOT select your fglrx driver yet - it might well be the cause of the problem.

If / When this works come back and let us know the results.

Secondly, is there a particular reason why you need that specific driver?  If you had a graphics screen before why did you feel the need to change the driver.  Was there something that the configuration would not do that you hope a new driver would give you?

---

### Post by onemind on 2006-12-10
Thanks,

I tried that but what driver do i choose? I choose ATI this time instead of flgx and it still doesn't work.

The reason i changed is so i could get more resolution choices. The highest resolution i could get was 1024x768 and i wanted higher and running that config thing let me choose higher res.

Any, i'll run the config thing again but what driver should i choose?

Thanks

---

### Post by onemind on 2006-12-10
Ok, I went back through again and chose the flgrx driver again but tried a different setting. I selected no to the framebuffer screen and now it works :)

Thanks

---

### Post by bscbrit on 2006-12-10
Great!  See you around the forum.

---

