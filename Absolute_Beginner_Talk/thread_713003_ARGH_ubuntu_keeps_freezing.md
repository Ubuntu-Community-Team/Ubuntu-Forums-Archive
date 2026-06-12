---
title: "ARGH ubuntu keeps freezing"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by benjaminjames on 2008-03-02
hi guys my ubuntu keeps freezing usually when im surfing the web it either freezes completely even the mouse or it freezes and i can move the mouse but not click anything i heard that it was a driver conflict but i dont have a clue. im running with amd 5200+ nvidia 7300le and its a dual boot with vista any help please i did think about reinstalling but im completely clueless with the manual install il try anything even an install if thats the easiest to explain thanks all

---

### Post by benjaminjames on 2008-03-02
guys forgot to mention this is happening every 15 20 mins i just had to reboot after i wrote that last message i really wanna give ubuntu a go but this is unworkable at the mo

---

### Post by astoltz on 2008-03-02
The first thing I'd suspect is the video drivers.  Are you using the restricted drivers for your nvidia card?

When it freezes, does pressing Ctrl-Alt-F1 do anything?  It should bring you to a login prompt where we can troubleshoot a little.  You can also try: Ctrl-Alt-Backspace to kill the x-server, or Alt-SysRq-K (kill everything running on the current session).

---

### Post by MONODA on 2008-03-02
are you running visual effects? if so trun them off they are causing the problem

---

### Post by benjaminjames on 2008-03-02
thanks guys will try that but how do i disable the driver is it just a case off turning the effects off or do i have to manually disable it???? also is there a work around for this because i would really like to have the accelerated effects although its not a must?? thanks again

---

### Post by benjaminjames on 2008-03-02
okay heres an update i turned off the restricted driver about an hour ago and so far no freezes :) hooray however i would like to be able to use the restricted driver so is there a work around or not guys any help appreciated

---

### Post by astoltz on 2008-03-02
> **benjaminjames said:**
> okay heres an update i turned off the restricted driver about an hour ago and so far no freezes :) hooray however i would like to be able to use the restricted driver so is there a work around or not guys any help appreciated
I'd try the latest driver from [nvidia]("http://www.nvidia.com/object/linux_display_amd64_169.12.html").  It's a couple versions past what's available in the repos for Gutsy.  I'm pretty sure there were some stability problems fixed - so it's worth a shot.  The instructions are pretty clear on the nvidia site - you will have to install the build-essential package to use the nvidia version however.  Lots of folks will recommend Envy to install the latest but I've never used it so I can't say. 

One thing to keep in mind.  If you do install a non-standard video driver (using Envy or otherwise) a kernel upgrade from Ubuntu will break the driver and you'll have to re-install.

---

### Post by benjaminjames on 2008-03-03
thanks for the reply i will definatly try this out but unfortunatley i got another freeze4 last night when trying to watch a video on youtube grrr is there any known preoblems with flash player freezing the computer?????

---

### Post by MONODA on 2008-03-03
i have heard of compiz having problems with flash so that it makes the computer crash. I suggest a re-install if possible or why not try out another distro :)? maybe mandriva or linux mint.

---

### Post by benjaminjames on 2008-03-03
yeah i would but the only problem i have is that i dont know how to manually do a re install i know im a bit of a silly but when it comes to the creat partion screen if i choose largest continuse free space will it replace my existing version of ubuntu or do i have to do something else

---

### Post by benjaminjames on 2008-03-03
Also im not running compiz at the moment

---

### Post by benjaminjames on 2008-03-08
ok so i took your advice and tried another disto mandriva and guess what its happening on this one too il boot up and if i try to play music or go on the net thats it the comp freezes and none of the alt sysreq k or contorl alt backspace thingys work just now i wasnt even running a program just resizing a window and boom another freeze any ideas guys?

---

### Post by Mud.Knee.Havoc on 2008-03-08
Completely get rid of 3d acceleration (ie. use the nv driver instead of nvidia) for a day and see if that helps.  I bet it does.

---

### Post by benjaminjames on 2008-04-02
thats not the point tho mate it definatley is the nvidia driver but i do not know how to get it working

---

### Post by halitech on 2008-04-02
> **benjaminjames said:**
> ok so i took your advice and tried another disto mandriva and guess what its happening on this one too il boot up and if i try to play music or go on the net thats it the comp freezes and none of the alt sysreq k or contorl alt backspace thingys work just now i wasnt even running a program just resizing a window and boom another freeze any ideas guys?

if you are freezing in another OS then it's not OS or driver related. Boot from the CD and run MEMTEST for about 8 hours. I'm thinking either you have a memory problem or you have a heat problem.

---

### Post by Ripfox on 2008-04-02
> **halitech said:**
> if you are freezing in another OS then it's not OS or driver related. Boot from the CD and run MEMTEST for about 8 hours. I'm thinking either you have a memory problem or you have a heat problem.

This definitely sounds like a hardware problem now.

---

### Post by halitech on 2008-04-02
> **ripfox said:**
> This definitely sounds like a hardware problem now.

to be honest I was thinking hardware problem when he said he turned off the driver and it didn't freeze as often :)

---

### Post by caeroe on 2008-04-08
Awhile ago I posted in this thread:  [http://ubuntuforums.org/showthread.php?t=587905&highlight=7300le&page=63](http://ubuntuforums.org/showthread.php?t=587905&highlight=7300le&page=63)

I also had the 7300LE with my setup, and a weak 300w power supply.  Gutsy 64 bit edition would freeze every 10min to an hour.

After upgrading to a 7600GS and a 480w power supply I haven't had any lockups.  It's been a couple weeks now with no issues, including playing games, Flash on websites, and Youtube.  Granted Firefox sometimes locks up, but not my entire system.

Unfortunately this topic is a few days old, so I may have missed the guy who started it.

---

