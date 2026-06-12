---
title: "Install stops after &quot;Kernel Direct Mapping..&quot;"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Premedicated on 2007-06-11
Basically when I try to install Ubuntu, it'll pop up the graphics interface asking if I want to install, repair, etc etc. I'll select install, it'll load a few things then get to the screen where it says 'Kernel alive' and kernel direct mapping tables up to 100000000 @ 8000-d000' then it will go to a completely black screen and just stop. No graphics or anything. I noticed the cd stops as well as any loading from the computer. I have a 300 gig harddrive, amd athlon 64x2 dual core processor, a GeForce 7900 video card, and a gig of ram. I believe I have enough to run this. Any help would be great. Thank you.

---

### Post by Random Roadkill on 2007-06-19
The same thing happened to me, except that I was booting from a hard drive and the screen did not go blank; it just froze with the text that you described.

---

### Post by Gareon on 2007-06-20
I just resolved the problem on my box. From the information I read on several posts on this forum and bug-reports from Google it seemed to be a problem with the splash screen. Mine installed fine and worked with no problems for a couple of days then I did some updates and installed the splash screen. The next start up hung at "Kernel alive direct mapping tables up to 100000000 @8000-d000"
The fix said to reboot > hit F6 > remove "splash" and add "noapic" to boot command. However when I hit F6 at start-up it just finished booting up.
I then went to Applications > Settings > Splash screen settings and set the splash screen to "none".
Rebooted and everything went fine.
Hope this helps.

---

### Post by crazydiver on 2007-06-20
My friend had the same exact problem and I fixed it by pressing F6 when the install part of the screen comes out. Although this might not work for all users, try replacing "splash" for "break=bottom"    .  Hopefully, this will work and everything will go fine... 


If this doesn't work at all, install in text mode or go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and select 64bit AMD and Intel computers right before clicking on the start download button. Burn the file onto a CD and try installing again!

---

### Post by Enginer on 2008-05-26
A late reply to this thread...

Installing 8.04 LTS, same thing happens.

JUST Before system locks up, hitting <F6> gets me past the lock-up point. (message flashes saying something about splash=quiet)

---

