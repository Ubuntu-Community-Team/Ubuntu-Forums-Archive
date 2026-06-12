---
title: "iLamp G4: LCD-insomnia?"
date: 2005-07-12
forum: Apple PPC Users
---

### Post by phibxr on 2005-07-12
Is there any way to put the LCD-screen in an iLamp to sleep under Ubuntu? When I lock the screen in Gnome, the backlight stays on.

It feels like leaving the LCD in this state for days could cause some serious damage. :-?

---

### Post by SpazTheCat on 2005-07-12
Hi,

AFAIK you can't turn off the backlight or powerdown the monitor. If I remember correctly, it has something to do with the video card in those iMacs.

But, if I'm wrong, I'd love to be corrrected. I have the same issue with mine.

Andy

---

### Post by bleedingpowers on 2008-07-13
3 years later...

Did any of you ever find a solution to turn off the display on a ppc g4 imac (iLamp)? I'm currently using ubuntu server 8.04 with xubuntu as a desktop manager. Everything else works (it even suspends properly). I just can't seem to find an answer to shut just the screen off. I've been looking around for an answer, but no luck yet.

---

### Post by stream303 on 2008-07-17
There is hope!  I had the same problem for years with my G5 iMac, and I don't know if it was a kernel upgrade or gnome power-management issue in Ubuntu Hardy, but the backlight on my internal lcd actually turns off now!

I was so used to it not working that I thought I had burned out the internal monitor somehow. :)  I couldn't believe it, but now I can use the power management feature for putting the screen to sleep.

I'm not sure if Xubuntu has released anything beyond the Hardy late-beta, so that might be part of the problem.  I'll have to check to see if they put out and actually update anything anymore for ppc.  I know Ubuntu still does updates for sure.

Your backlight hardware might be different than mine - I'm not sure, so this may not work, but seeing that lcd screen actually go to sleep (and not just a blank screensaver) after years blew my mind. :)

---

### Post by bleedingpowers on 2008-07-18
Even with the Ubuntu desktop installed, I can't get the monitor to turn off. The backlight still stays on.

Are you using any special power manager such as "pmu" (pmud) besides the default one? Perhaps, you have installed something like that in the past that may be making the difference this time.

Anyway, I still hasn't lost hope...I'm even thinking to somehow attach a switch to the power cable for the monitor, but I guess I would have to take this machine apart again...and you perhaps realize that this is not such a pleasant job. I have take it apart in the past, but it's a pain to put it back together...I guess I'm just being lazy and afraid that this hack might not work, because I guess Apple doesn't like to make things hackable for the ultimate users like us.

---

### Post by stream303 on 2008-07-19
> **bleedingpowers said:**
> Even with the Ubuntu desktop installed, I can't get the monitor to turn off. The backlight still stays on.

I'm going to ask a dumb question - have you moved the slider in the Ubuntu gnome display power-management prefs to something smaller?  running and ducking ....

NOTE: although I can get my screen to sleep with no backlight, if I try to enable putting the system to sleep, it will eventually crash, so unfortunately for me, I can't put the computer as a whole to sleep and so I move the slider all the way to the right to disable that.  But at least the screen backlight turns off.

> Are you using any special power manager such as "pmu" (pmud) besides the default one? Perhaps, you have installed something like that in the past that may be making the difference this time.

Well, I did remove powernowd, and install CPUDYN as my cpu frequency-scaler.  I found that with powernowd, it would never scale down, but with cpudyn it would.  Not sure if there is any interaction here with the backlight, but worth mentioning.  You may want to check this yourself by adding a cpu-frequency monitoring applet in either the top or bottom panel (right click on either top or bottom panel and add the applet).  Again I doubt this has anything to do with the backlight, but stranger things have happened to me in ppc land. :)

The backlight stuff is actually in the kernel, so maybe search and see "G4 iMac ppc backlight" turns up anything regarding kernel support.  Apple doesn't seem too interested in making it easy for our kernel developers.....

I wouldn't take the machine apart just yet.  Note that I have also done a pmu/smu reset on the box just to make sure I was starting from a clean slate - and again not sure if this would affect the backlight capabilities since I'm not at that low-level with Apple PPC hardware.

---

### Post by bleedingpowers on 2008-07-19
Thanks for your devoted concern, stream303:

I have play with the times in the sliders to see if it makes a difference, but no luck with that.

I have even attempted to turn off the display with commands like the following:
```
xset dpms force off
```
but I just get a semi-orange/yellow screen. The backlight doesn't turn off.

What I'm planning to do is to follow your steps about reseting the PMU
> I wouldn't take the machine apart just yet. Note that I have also done a pmu/smu reset on the box just to make sure I was starting from a clean slate

I found how to do this at [http://support.apple.com/kb/HT1712?viewlocale=en_US]("http://support.apple.com/kb/HT1712?viewlocale=en_US")

I hope it works, I'll let you know about my results later.

---

