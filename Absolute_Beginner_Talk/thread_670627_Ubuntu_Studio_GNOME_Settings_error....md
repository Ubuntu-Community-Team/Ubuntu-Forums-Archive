---
title: "Ubuntu Studio GNOME Settings error..."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ~Maxx on 2008-01-17
Okay...  I just got tis installed after much hassle, and I've gone and broken it already!  Today I reinstalled Feisty, Upgraded to Gutsy, then upgraded to Studio.  Once that was done I edited a few of the fonts, changed to the Ubuntu Studio theme, and edited the boot manager so XP was first (for my fiance  ;) ).  I restarted to make sure the boot manager was set the way I wanted it to be, and after logging back into Ubustu I got the following error message...
> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
And the Ubustu theme does not seem to have loaded (while new desktop background and fonts are intact).  I checked the "Screens and Graphics" settings and they seem to be fine (plug & play monitor, 1280x1024 res @ 75Hz).  It seems impossible that I could have done anything wrong at this point.  Anyone know what the error message is about and how to fix it?

Thanks a bunch...

---

### Post by spiderbatdad on 2008-01-17
this doesn't look like you broke anything, and should be fine after re-boot. The first part of that message can be caused by a lot different simple start up issues, and you probably wont see it again for a long time. The second part looks like a networking issue. You may need to look at system daemon logs if it persists.

---

### Post by ~Maxx on 2008-01-17
Thanks for the fast response!  I rebooted and got the same message.  So I went ahead and chganged my settings from plug & play monitor to 1280x1024 LCD (which left me no option other than 60Hz rate).  Logged out, then back in and changed settings back to original.  Restarted and all is well (for) now.  

There may be some oddities detected with my network as I have not yet configured my second machine (Xubuntu box) for it.  Router is still plugged in for net access on both, but can't share files yet.

Hopefully this will not persist.  Thanks again for your reply!

---

