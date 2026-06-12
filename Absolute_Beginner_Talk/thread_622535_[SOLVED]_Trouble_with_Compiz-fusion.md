---
title: "[SOLVED] Trouble with Compiz-fusion"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Clark76 on 2007-11-24
Hello

I recently upgraded from 7.04 to 7.10 from the Update Manager.  After updating I decided to try out Compiz-fusion.  I never got it to work in 7.04 but since it was "built-in" with 7.10 I waited for its release since I felt I must be doing something wrong.  Since the upgrade, if I click on CompizConfig Settings Manager nothing happens.  I could get in to it when I was still at 7.04.  I have gone into Restricted Drivers Manager and enabled the driver for my NVIDIA card but still nothing.  Not sure where to go from here.  Please let me know if there is any more info needed.  Any help offered is appreciated but be warned I am fairly new to Ubuntu.
Thanks

---

### Post by ijason on 2007-11-24
compiz worked out of the box for me, on a fresh 7.10 install. but what did NOT work out of the box was using compiz with the 'restricted drivers' enabled. it only worked with the default drivers being used. to get compiz working for me in conjunction with my advanced drivers i had to install XGL. 

how do you feel about doing a fresh 7.10 install? i've heard lots of people saying a fresh install works better. and i know that the nvidia cards are much better supported than ATI, so i would think it would work out of the box.

---

### Post by corevette on 2007-11-24
try enabling it in: system -> preferences -> appearance -> desktop effects
that's defaultly where it is now in ubuntu

---

### Post by Majorix on 2007-11-24
Do you see System > Prefs > Advanced Desktop Effects Settings? That is compizconfig-settings-manager.

---

### Post by Clark76 on 2007-11-25
> compiz worked out of the box for me, on a fresh 7.10 install. but what did NOT work out of the box was using compiz with the 'restricted drivers' enabled. it only worked with the default drivers being used. to get compiz working for me in conjunction with my advanced drivers i had to install XGL.

how do you feel about doing a fresh 7.10 install? i've heard lots of people saying a fresh install works better. and i know that the nvidia cards are much better supported than ATI, so i would think it would work out of the box.

I have not done much in this install so I would not object to a fresh install unless someone had any other ideas.

> try enabling it in: system -> preferences -> appearance -> desktop effects
that's defaultly where it is now in ubuntu

There is no desktop effects.  If I go to system -> preferences -> appearance, there is a [COLOR="Blue"]visual effects[/COLOR].  Under visual effects the choices are none, normal, extra and custom.  It is set to none and if I try to change it to anything else, the window goes gray for about a minute then resets back to none.

> Do you see System > Prefs > Advanced Desktop Effects Settings? That is compizconfig-settings-manager.

No it is not there.  I remember it being there for 7.04 but now it is missing and CompizConfig Settings Manager is listed under Preferences.

---

### Post by tiachopvutru on 2007-11-25
I would suggest doing a fresh install... You may run into other issues later on even if you fix this one. (Well, from what I've heard, anyway)

But have you tried installed XGL? If not, do
```
sudo apt-get install xserver-xgl
```

---

### Post by FuturePilot on 2007-11-25
> **tiachopvutru said:**
> I would suggest doing a fresh install... You may run into other issues later on even if you fix this one. (Well, from what I've heard, anyway)

But have you tried installed XGL? If not, do
```
sudo apt-get install xserver-xgl
```

You do not need XGL if you have a Nvidia card.

If you had Compiz Fusion installed on Feisty and did an upgrade to Gutsy, most likely you have conflicts which is why it's not working. Go through Synaptic and purge (not just remove, but completely remove) anything related to Compiz, then reinstall it.
[http://ubuntuforums.org/showthread.php?t=580063]("http://ubuntuforums.org/showthread.php?t=580063")

---

### Post by Clark76 on 2007-11-29
Sorry for the delay everyone.

I first purged everything related to Compiz then reinstalled it.  I was still having problems so I decided to do a complete reinstall of Gutsy - the system is a dual boot with Vista if that makes a difference.  My new problem is that I now have no cursor.  When running from the live CD it worked but after the install the cursor is gone or invisible might be a better word.  When I move the mouse around certain icons on the desktop will light up and I am able to click them.  Any ideas?

---

### Post by Clark76 on 2007-11-29
I realized that I have asked a different question from my first that others might not realize from the title of this thread.  Since I believe my first problem should be resolved (hard to tell without a cursor;)) I will mark this topic as solved and start a new thread for my problem with the cursor.  Thank you.

---

