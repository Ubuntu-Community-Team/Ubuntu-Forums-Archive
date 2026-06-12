---
title: "Ibook G3 Dual USB Ubuntu Help"
date: 2010-06-04
forum: Apple Hardware Users
---

### Post by coolcourt on 2010-06-04
Hello I just installed 10.04 LTS PPC from ubuntu's server

My comp has 128mb ram 500mhz G3

My problems are.

Screen - cant find a solution to get the screen resoulution 

Speed - I believe the gnome is beyond too much for the G3, lookin for an alternative or a method of installing a lightweight shell to run basic apps, eclipse (maybe) and Firefox

Kernel info, not sure if i should be trying to upgrade or if there is even an update.

There are many issues and i would love to help and write up how we could restore and use some of these old computers. lots of schools have many old apples just collecting dust.

All help would be appreciate.

I just need to get pointed in the right direction to get my first installation set up while i still can afford to leave my ibook hooked up to the cord in a high traffic area

---

### Post by conal on 2010-06-04
If you need a window manager LXDE might just run - I have an old laptop running LXDE on 192mb ram/333Mhz processor with no problems at all.  As for resolution you might need to change the xorg.conf file - if you search this forum you'll find other people have posted their xorg.conf files for these iBooks.


P.S I'd recommend Linux Mint PowerPC as it has less bugs.

Cheers

Conal

---

### Post by sha.goyjo on 2010-06-05
If you have the gumption, I'd advise you to get the powerpc mini.iso and build your system from the ground up. You'll start out with no x, no nothin, and then you can build a very lightweight system on top of it. I've built very speedy (and current) setups for the old fruit colors imacs this way. And since they have 233mhz processors, I think it may work out well for you.

As for window managers to put on top of your bare-bones ubuntu install, I'd recommend going REALLY light. But that's just me, I prefer speed over glam. IceWM is about as fast as you can get and still have the necessities. I recommend it highly for a machine of your era. She'll fly.

Also, instead of using a fullweight music player, try running mpd (music player daemon) and using one of the many graphical frontends for it. It runs VERY light.

And, I know this is apocryphal to say on an proper Linux forum, but Opera works great on older PowerPC systems.

Other than that, just use your own best judgement. There are many good lightweight alternatives to the heavier programs that most people use on modern computers. I do refurbishing and donation of old systems as a community service project, and most of the stuff we see is from the era that you are currently working on, so I can certify to you that it is very possible.

As for screen resolution for the G3, there are a lot of threads around here with people working on those kinds of issues, but if you are serious about fixing it you need to give some information regarding what you have and have not tried so that we know where to start.

Jason

---

### Post by rjcalifornia on 2010-06-05
> **coolcourt said:**
> Hello I just installed 10.04 LTS PPC from ubuntu's server

My comp has 128mb ram 500mhz G3

My problems are.

Screen - cant find a solution to get the screen resoulution 

Speed - I believe the gnome is beyond too much for the G3, lookin for an alternative or a method of installing a lightweight shell to run basic apps, eclipse (maybe) and Firefox

Kernel info, not sure if i should be trying to upgrade or if there is even an update.

There are many issues and i would love to help and write up how we could restore and use some of these old computers. lots of schools have many old apples just collecting dust.

All help would be appreciate.

I just need to get pointed in the right direction to get my first installation set up while i still can afford to leave my ibook hooked up to the cord in a high traffic area

Take a look at this,  and tell me how it goes...

[http://ubuntuforums.org/showthread.php?t=1265921](http://ubuntuforums.org/showthread.php?t=1265921)
:guitar:

---

### Post by sha.goyjo on 2010-06-06
If you are bound and determined to try vanburen's advice, I advice also trying icewm. kde is known to be one of the heaviest (up along with gnome) DE's in existence. If you want something really light for your older machine, I'd advise against picking up a full fledged DE. If you must use a DE, use the lubuntu-desktop package. But again, I'd advise a simple window manager instead.

---

