---
title: "x60 tablet wacom stylus doesn't rotate"
date: 2012-03-28
forum: Any Other OS
---

### Post by thedaikini on 2012-03-28
Hi Favux,   I've recently purchased an X60t and loaded LM12. My display rotates, but the stylus is still messed up. Any ideas? I've used rotate.sh from Luke Campagnola's site, and I've tried the suggestions here, but nothing seems to work.   Any more comprehensive scripts available that will save me from terminal work with every screen movement?  Thanks for your help!  I decided I should give you my specs:  Lenovo Thinkpad X60t (6363-AB7) Core Duo (1.66 x2) Intel 945GM x86/MMX/SSE2 32-bit LM12

---

### Post by Favux on 2012-03-28
Hi thedaikini,

Welcome to Ubuntu forums!

Magick Rotation should do the trick:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Also see the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

With Mint 12 (Oneiric) you still have the Portrait orientation bug in xf86-input-wacom so if you use Portrait orientation in tablet mode you'll want to update it.  See part II. on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or the FAQ on Magick Rotation.

---

### Post by thedaikini on 2012-03-28
Thank you for the quick reply, Favux.  I download the tar.bz2, opened the Readme and began the install.  I get an error saying that I haven't installed libx11-dev, which is marked as installed. For good measure, I reinstalled it to no avail.  Any ideas?  Thanks again!

---

### Post by Favux on 2012-03-28
Yes.  It is case sensitive and in Mint you have to use libX11-dev.  Why Mint decided to use a capital X I have no idea.

---

### Post by thedaikini on 2012-03-28
Where is that package called out? Do I need to mod a script?  Thanks again  EDIT: I modified the installer file to libX11-dev and install completed. However, the stylus is still not rotating correctly.

Edit 2:  ~/xf86-input-wacom-0.14.0 $ make
make: *** No targets specified and no makefile found.  Stop.
[user]  ~/xf86-input-wacom-0.14.0 $ sudo make install
[sudo] password for [user]: 
make: *** No rule to make target `install'.  Stop.

---

### Post by Favux on 2012-03-28
Is that the Magick Installer file you modified?  The Mint Installer fix is in the latest devel revision.  I'm in the middle of preparing some pushes to devel and unstable.

The configure went OK?

I just cloned the xf86-input-wacom git repository on Maverick without a problem.  Don't think I've tried compiling xf86-input-wacom-0.14.0 in Oneiric.  I'll have to test that.  Running 0.13.0 on my tablet PC anyway.


Edit:  Nope, no problem compiling the xf86-input-wacom-0.14.0 tar in Oneiric.  So it is not a tar release problem.

---

### Post by Perfect Storm on 2012-03-28
Moved to Other OS/Distro Talk.

---

### Post by thedaikini on 2012-03-29
Thanks for all the help, Favux. I modified the installer file to call out libX11-dev rather than libx11-dev. The install worked. However, I downloaded the tar and began the build on xf86-input-wacom-0.14.0 when it ran into the error above. I haven't tried git. I'll do that now and let you know...

---

### Post by thedaikini on 2012-03-29
Thank you very much, Favux! The git method worked. I'm not sure why the tar build didn't take, but the stylus now tracks accurately when in tablet mode. Great work! Thank you again!

---

### Post by Favux on 2012-03-29
Great!  :)

Sounds like you are good to go.

---

