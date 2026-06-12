---
title: "Screensavers are not working :("
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-02-01
Hi guys I'm having a little trouble getting any screensaver other than 'blank screen' to work.

I have checked the activate screensaver when idle box, and my system is configured so that the screensaver will kick in after 1 minute and the display will go to sleep after 5 minutes.

Anyway no matter what screensaver I select, all I get is a blank screen -- a pity because I really like the look of that Glmatrix one :)


Btw, the preview of the screensavers works fine. I'm running w/ the nvidia driver from the repos (not the beta one) and I've got my defaultdepth set to 24 (if that has anything to do with it). I'm not running anything fancy (like beryl or compiz).


Any suggestions would be much appreciated.
Cheers!

---

### Post by Patrick-Ruff on 2007-02-01
nvidia drivers? wtf, I've never heard of anything like this happening. this is when you should begin to question do you /really/ need them?  

also, you could try running AIGLX (and beryl if you want ;)  ) it could help.

---

### Post by deadgobby on 2007-02-01
> **dr_d said:**
> Hi guys I'm having a little trouble getting any screensaver other than 'blank screen' to work.

I have checked the activate screensaver when idle box, and my system is configured so that the screensaver will kick in after 1 minute and the display will go to sleep after 5 minutes.

Anyway no matter what screensaver I select, all I get is a blank screen -- a pity because I really like the look of that Glmatrix one :)


Btw, the preview of the screensavers works fine. I'm running w/ the nvidia driver from the repos (not the beta one) and I've got my defaultdepth set to 24 (if that has anything to do with it). I'm not running anything fancy (like beryl or compiz).


Any suggestions would be much appreciated.
Cheers!

 Once a while my screen saver will not pop up in Edgy. It really does not bother me, because the monitor will go to sleep a bit after that. I do not run any graphics card yet. I am going to get one because they are on sale because of the Vista push. Nvidia is nice. Perhaps it will be fix by April.
Gobby

---

### Post by dr_d on 2007-02-01
sure i dont 'really' need them. but i'd like to know if this is a problem others are having or if there is something wrong with my installation (which is fairly new).

---

### Post by poohbear1616 on 2007-02-01
In Edgy I had problems with the screensaver not working when edgy first come out. I think alot of folks had this problem. btw I use an ati card.

---

### Post by dr_d on 2007-02-01
oh well that's good to know...

presumably it will be fixed eventually... and until then i should be just fine with the 'blank screen' option.

---

### Post by mver on 2007-02-02
I have the exact same problem you describe in the first post in this thread dr_d.  I'm running 6.10 Edgy with integrated intel graphics.  Its not a big problem but hopefully someone fixes it sometime.

---

### Post by K.Mandla on 2007-02-02
You might check if you have the *xscreensaver-gl-extra* and *xscreensaver-data-extra* packages installed. You probably do, but one never knows. :-k

---

### Post by mver on 2007-02-02
I checked and both of those packages were not installed so I installed them but the problem is unchanged.

---

### Post by dr_d on 2007-02-21
hmm.. let's hope it's fixed in feisty :)

---

### Post by itchanddino on 2007-02-21
See if this post helps

[http://ubuntuforums.org/showthread.php?t=288651&page=5&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=288651&page=5&highlight=screensaver)

---

### Post by K.Mandla on 2007-02-21
:-k I'm still thinking about this one. If the preview works, why doesn't it work in fullscreen? You don't have the timing set so it goes straight from the screensaver to screen timeout, do you? That might account for why the screensaver never shows up -- if the monitor powersave is set to the same interval as the screensaver. 

Just thinking out loud again. :-k

---

### Post by dr_d on 2007-02-21
itchanddino - thanks for the link, but i think id rather wait for the devs to fix this rather than messing around recompiling stuff and possibly break something..

 K.Mandla - it's a good theory but no dice..monitor turns off after 5 mins, screensaver kicks in (or rather doesn't) after 1min

:confused:

---

### Post by proset on 2007-02-25
I've got the exact same problem.  Another note is that the screensavers work fine on certain resolutions for me.  In other words, if I'm at 1280x768 they work.  They seem not to work on the "extra" resolutions that NVIDIA is offering.

thanks,

ew

---

### Post by dr_d on 2007-02-25
hmm my resolution was set to 1920*1200 out of the box (even before installing nvidia drivers).

---

### Post by proset on 2007-03-08
I've resolved the issue by reinstalling the screensaver packages with the package manager application.

I think I may have gotten into this situation through the following steps.

1.  Installed Ubuntu using onboard video and a TV monitor.  Only resolutions up to 1024x768 were supported by that setup.  Screensavers worked fine.

2.  Changed configuration to a new video card and a monitor that supported higher resolutions.  Screen resolution application in Preferences only displayed originally installed resolution settings.  Screensavers worked fine.

3.  Figured out how to reflect the increase in supported resolution settings in the Screen Resolution application (I forget exactly how I did this, sorry, but it was a command line exercise).  Monitor worked with new settings but no screensaver although they did work in preview mode.

4.  Reinstalled screensaver packages and everything is working.

So to me it seems that the OS is not picking up the fact that new video card and monitor capabilities are present in all dependent apps.

thanks,

proset

---

### Post by undertakingyou on 2007-03-08
> **itchanddino said:**
> See if this post helps

[http://ubuntuforums.org/showthread.php?t=288651&page=5&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=288651&page=5&highlight=screensaver)

This may look overwhelming but it really is quite easy, and fixed this issue for me quite nicely.

---

### Post by motorious on 2007-03-08
<------linux/ubuntu newb here trying to make the transition from windows

I'm loving edgy, but am having the exact same problem.  I am running 6.10 (edgy eft) and have a Radeon Mobility U1 on a EVO N1015v.  The screen savers worked great in dapper but not in edgy.  I tried to enable direct rendering since it's not supported but no luck.  Installed the two packages mentioned above and no luck.  If anyone has a fix or update please post.

Thanks

---

