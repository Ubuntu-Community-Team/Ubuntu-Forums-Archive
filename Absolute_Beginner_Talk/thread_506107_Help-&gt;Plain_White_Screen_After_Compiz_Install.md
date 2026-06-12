---
title: "Help-&gt;Plain White Screen After Compiz Install"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by vzxa1 on 2007-07-21
I installed Compiz, restarted the computer and now I have a plain white screen looking back at me(hence no way of correcting the problem in the normal start up mode).  I suppose I should boot up in safe mode and uninstall Compiz, but I'm quite the novice and my knowledge is very limited.  Is there an easier way ie. a recovery option as in MS XP?   Can anyone please provide me with the correct commands to fix the problem?  

As always any help will be appreciated.

---

### Post by ramjet_1953 on 2007-07-21
What video card / chipset do you have?

Did you download the drivers for that card?

Is direct rendering enabled?

Regards,
Roger :cool:

---

### Post by vzxa1 on 2007-07-21
Hiya Roger 

Thanks for the reply, the laptop that's causing all the commotion is an old entry level Advent model(Generic UK brand  - SiS Mirage Graphics [Display adapter]Default Monitor).  I am not at all surprised that compiz/Beryl don't work, I just figured there would be a facility to undo the chosen option.  Really, I'm not all that bothered about the fly interface, I basically just want to be able to run Ubuntu as before.

Thanks, keep 'em coming.

---

### Post by vzxa1 on 2007-07-21
Right

I think I just shot myself in the foot, 

This is what I did in the Recovery Mode:

$ sudo apt-get remove compiz

$ sudo apt-get remove beryl

$ sudo apt-get autoremove

Starting up my screen is as white and as blank as ever, is there an alternative here or do I have to reinstall Ubuntu? (don't really want to as I'll be losing oodles of work - *where's my Prozac?*:shock:)

Any help will be appreciated

---

