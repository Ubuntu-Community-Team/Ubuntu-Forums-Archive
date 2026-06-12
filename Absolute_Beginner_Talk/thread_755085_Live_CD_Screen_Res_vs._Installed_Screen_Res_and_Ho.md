---
title: "Live CD Screen Res vs. Installed Screen Res and How to Fix"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by youngheart80 on 2008-04-14
Hey all,

Been wanting to install a Ubuntu variant for a while and finally did - Xubuntu 7.10.  I've run into a bit of a snag - installation with the LiveCD was a breeze - very easy and simple.  I did forget to reconnect my internet during the install so missed the security updates, but got them after.  However, when I rebooted, I got a little notice window telling me that Ubuntu was loading in low graphics mode.  I tried to configure there and then later after the boot completed - no luck.  Max. screen resolution is 800x600.  But during the LiveCD, resolution is great at 1600x1200.  I've tried installing new drivers, redoing the autodetect, and a couple of other things listed on other forum posts.  Haven't yet edited Xorg directly - that's probably the next step.

However, the quirky thing is if I boot back into the LiveCD, the same great 1600x1200 resolution appears.  If I reboot out of the LiveCD back into the installed version, the screen resolution sticks - still 1600x1200 and I can adjust it to whatever I want.  BUT, if I shutdown/restart from there, the next time I log in, the "low graphics" notice reappears and 800x600 is back with no way to change.

So, two questions: 
1.  Is there anyway to get the changes to stick? and/or
2.  Is there anyway to just get whatever the settings are from the Live CD and use those?  Cause they obviously work.

_Computer Specs:_
Xubuntu 7.10
Video Card - integrated NVIDIA TNT2  4x AGP w/ 16Mb memory
Monitor - Gateway EV910

---

### Post by Gulyan on 2008-04-14
i got the same prolem on ubuntu 7.10
the solution was a reinstall :popcorn:

---

### Post by youngheart80 on 2008-04-14
Hmm...  Oh well.  It's not like the install time is that long compared to WinXP like I'm used to.  Since it's still such a fresh install, I guess there's really nothing to loose.  I'll try it when I get home tonight.

---

### Post by youngheart80 on 2008-04-15
No luck - acts exactly the same as before.  Any other suggestions?  I will go through the redetect and other things I had done before.  Using the restricted NVIDIA legacy driver.

What really confuses me is how it works just fine the first reboot after using the Live CD - shouldn't everything clear out of the RAM, etc. during a reboot?  Why would it work the reboot immediately after using the Live CD but not the reboot after that?

Is there a way I can check to see what driver the LiveCD is using when booted?  Maybe I'm just installing the wrong driver after.

---

### Post by kpkeerthi on 2008-04-15
From GRUB, boot into Recovery Mode.
At the prompt, type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now choose **nvidia** for driver and **1600x1200** for resolution.
Type **reboot** and boot normally.

---

### Post by youngheart80 on 2008-04-15
I'll give that one a shot - haven't done it from the recovery mode yet.  Will try this evening when I get home.

---

### Post by youngheart80 on 2008-04-16
Okay, more weirdness.

I got home last night - computer had been shut down all day.  I turn it on, boot up, and now everything works just like it's supposed to.  Correct drivers, correct screen resolution, everything.  And I didn't do anything else.  I'm thinking there is something weird happening with the restart not flushing out the memory or something.  When I get some time, I'll experiment with it to see if I can get it to happen repeatedly.  For now thought all seems good.

If when I boot up tonight everything is still good, I'll change this to a "fixed" thread.  Thanks all.

EDIT:  Update - seems the problem is being caused by changing the screen resolution from 1600x1200.  If I go to anything else, it throws the error and I have to use kpkeerthi's solution to get anything larger than 800x600.  That does work to get it back, but oddly, I don't get to choose a resolution and driver - it just automatically does it.  Right now, this is good enough, but at some point I'm going to want to go to slightly larger resolution for my wife's sake.

---

