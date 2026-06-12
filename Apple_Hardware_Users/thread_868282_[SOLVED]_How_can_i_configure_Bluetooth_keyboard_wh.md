---
title: "[SOLVED] How can i configure Bluetooth keyboard when I can't even log on?"
date: 2008-07-23
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-07-23
Hi,
  I bought the bluetooth keyboard for my 24" iMac, but with Ubuntu, I can't even log on yet. 

So given that it isn't configured yet with Ubuntu, how do I configure it when I can't even log in? Must I use a regular keyboard to piggy back my way in or is there another way?

I appreciate any pointers. Meanwhile, I'll hook up my regular keyboard and see what can be done.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-07-23
Nevermind,...Got it!  I followed this HOWTO:

 [http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

---

### Post by cyberdork33 on 2008-07-23
does that stay through a reboot?

A bug has been reopened against Intrepid about not having hidd included anymore. You might want to watch this bug:
[https://bugs.launchpad.net/bugs/191704](https://bugs.launchpad.net/bugs/191704)

---

### Post by Brightbelt on 2008-07-23
Thanks Cyber, for the heads up. I did do a Log out; at least going to the login screen I could still type.

I'm not at my computer now, but I'll try logging on later. One question, though: Just by doing Ubuntu updates, am I upgrading to Intrepid automatically? Or will it be a full upgrade?

Many Thanks for your help,....Frank B.

---

### Post by Brightbelt on 2008-07-24
I am typing from the bluetooth keyboard now, so yes, this definitely held through a reboot. Nice surprise.

---

### Post by cyberdork33 on 2008-07-24
> **Brightbelt said:**
> I am typing from the bluetooth keyboard now, so yes, this definitely held through a reboot. Nice surprise.
Well that's good. I still have issues with my keyboard (older white style).

You will be prompted to upgrade to Intrepid when it is released. Upgrading in this way doesn't usually work correctly though. I just do full installs on each release after backing up files in my home directory.

---

### Post by Brightbelt on 2008-07-24
One thing to add, FYI: the keyboard works, but it does get quite a bit sluggish at the rEFIt menu when I'm booting. 

Also Cyber, do you copy your home directory to an external drive etc on a new install? I can't imagine it would survive a fresh install/reformat. 

But I'm not an expert either, so I could easily be missing something...

Thanks, Frank B.

---

### Post by cyberdork33 on 2008-07-24
> **Brightbelt said:**
> One thing to add, FYI: the keyboard works, but it does get quite a bit sluggish at the rEFIt menu when I'm booting. 

Also Cyber, do you copy your home directory to an external drive etc on a new install? I can't imagine it would survive a fresh install/reformat. 

But I'm not an expert either, so I could easily be missing something...

Thanks, Frank B.
Yea I just copy my pictures/docs/videos onto a fileserver I have. then reinstall.

The way you _should_ do it is create /home on a separate partition, then you just don't format it on new installs. The beauty of being able to mount a partition on a folder :) (HINT: you can actually pull this off in OSX too, though it takes a bit more configuration). I find that some of the config files in your home directory can cause problems after an upgrade though. This is probably more likely due to the fact that I test alpha / beta releases of Ubuntu...

---

