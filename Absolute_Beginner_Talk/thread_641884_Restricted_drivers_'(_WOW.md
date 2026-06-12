---
title: "Restricted drivers :'( WOW"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-12-15
Hey, I have a friend that has a problem I've never seen: as follows.

He needs to enable two restricted drivers under the restricted drivers manager.
One is **"ATI accelerated graphics driver**" which comes with the following error when I try and  enable it "**The software source for the package xorg-driver-fglrx is not enabled.**"

The second is for his wireless card driver "**Firmware for broadcom 43xx chipset family**" which has this error "**The software source for the package bcm43xx-fwcutter is not enabled.**"

I looked under synaptic for the packages and I think there already installed. So How do I enable them?????? ANY HELP WOULD BE GREATLY APPRECIATED.

THANKS IN ADVANCE  :):):):popcorn:

---

### Post by LaRoza on 2007-12-15
Can you just enable them? If it is the same as last time I saw it, the restricted driver manager let you enable drivers.

---

### Post by thelatinist on 2007-12-16
You need to enable the universe, restricted, and multiverse repositories.  System > Administration > Software Sources.  Check the appropriate boxes.

---

### Post by Sef on 2007-12-16
> You need to enable the universe, restricted, and multiverse repositories. System > Administration > Software Sources. Check the appropriate boxes.

Also you can enable all the repositories this simple way:

Applications > Add/Remove > Change the box in the top right corner to "All Available Applications".

---

### Post by thelatinist on 2007-12-16
> **Sef said:**
> Also you can enable all the repositories this simple way:

Applications > Add/Remove > Change the box in the top right corner to "All Available Applications".

True.  But I believe he was using Synaptic, so I thought I'd point him that way.

---

### Post by Sef on 2007-12-16
> True. But I believe he was using Synaptic, so I thought I'd point him that way.

What you did was fine.  I always like posing the easiest solution possible because someone else (like someone new to Ubuntu) might read it and have an easy solution to their problem.

---

### Post by jfank on 2007-12-16
What if you go into the restricted drivers settings and log in as the admin (root password required) and then click the box to enable them and the add/remove program will automatically install the updates for it?  I had to do that myself today with the driver for my video card to enable it.  You will of course have to restart computer after you do all of this.  This might be another step, and can be a little difficult for new users.  Just another option.

---

### Post by ~/Chromekaldra/~ on 2007-12-16
I'm having the same issue and what all of you have said isn't working for me. Add/Remove, the repostory doesn't show up. Restricted drivers only allows you to enable, but it (my ATI card) is still not in use. How do i use it? I've already done aticonfig and such, but no go.

When i go to change my graphics card to it, and test, i get a checkerboard screen (really fine) and then when i return, all that is black is now bright green. 

When i go to the ATI control center, it says it can't find the driver, but i know installed it yesterday...

And sorry to steal this thread, but seeing as we have similair problems i thought it'd be best to kill two birds with one stone rather than have me make a new thread...

---

### Post by thelatinist on 2007-12-16
Try System > Administration > Software Sources.  Check the appropriate check boxes.

---

### Post by ~/Chromekaldra/~ on 2007-12-16
I did, and multiverse/universe are checked. I'm using the Canadian server though...i'll try Main server and see if the repository pops up...if it even makes a difference. 

Isn't there code or something to find the repository or at least make my system recognize it? The file is right on my desktop...

*EDIT*

It didn't work.

---

