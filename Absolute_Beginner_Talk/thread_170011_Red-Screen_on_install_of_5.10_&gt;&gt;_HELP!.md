---
title: "Red-Screen on install of 5.10 &gt;&gt; HELP!"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Theo-Ubu on 2006-05-03
(tried posting this in Mac sub-forum, but nobody seemed to have an answer)

Hello,

I put in a fresh 10Gig drive (it was used, but I think wiped by the store...) in this iMac G3 Rev-A with aprox 100Mb of RAM and tried to install from CD. Somewhere along the way, all seems to be going fine, then I hit a red-screen saying something to the effect of:

"unable to install initrd-tools"

"check /target/var/log/bootstrap.log"

I try to continue on past that point through the blue-screen menus, but then I come to:

[!!] failed to install base system

Anybody have some clues for me as to what's happening or going wrong? Perhaps there's not enough memory to unpack the base system packages? It told me on a couple of occasions that old verions of the files existed, and did I want to overwrite them...?

Thanks!

---

### Post by Theo-Ubu on 2006-05-03
Oh please... just a little help?

---

### Post by Theo-Ubu on 2006-05-03
OK.  I've tried to do some diligent searching and I found a page that states that you need to be connected on a network to the wider internet for the installation process to work from a CD.  It apperently needs to go out and grab additional components or packages.

I am not connected to a network, so is this the likely cause.  Is this really true, or was the web-page wrong?:

[http://lowendmac.com/crews/05/1214.html](http://lowendmac.com/crews/05/1214.html)

The only other thing I can come up with is that perhaps the CD was burned at to fast a rate and I should try one burned at lower than 8x or something.

Are there ANY real ubuntu users with knowledge in this forum, or are we all just a bunch of newbies shouting into the void, unable to really help each other?

---

### Post by Sandlst on 2006-05-03
When installing, once it fails and spits you out to the blue-menu screen, you should be able to select an option at the bottom that reads something like "Check the cd for defects"  do that, and it will tell you if you have a bad cd or not.  I always burn ubuntu cds now at 4x, and even so, I have problems with them all the time-I can usually count on an install cd to work once, then suddenly for no apparent reason become 'corrupted'-at that point, the cd will ALWAYS fail at installing the base system(for me at least).  Good luck!

---

### Post by nalmeth on 2006-05-04
Despite what you might have heard, you can install without an internet connection, but you won't get the complete, up to date packages.
You should get the base system, and the gnome desktop environment.
Try downloading a new image, and burn it at a slow speed and try again. 
Are you trying to install the AMD64 kernel? Then try the generic i386 one.
Post back with your progress.
There are a lot of smart folks around here, I guess somedays it takes a while for them to wander to this area.
You might have more success with response in the Installation / Upgrade help area

---

