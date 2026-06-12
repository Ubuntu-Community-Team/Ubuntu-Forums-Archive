---
title: "Serpentine Burn button doesn't work"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2006-12-18
Hola.  Upgraded to edgy a while ago and don't think i've tried to burn a cd with serpentine since then, that is, until yesterday when I tried and i pressed the 'burn' button and it did jack.  I mean, you press it and absolutely nothing happens.  eventually burned using rythymbox but would much prefer to use serpentine.  anyone have any ideas on what i can do?  i'm a noob so be gentle. 

thanks!

---

### Post by angelsneverdie on 2006-12-19
still no ideas. . . still doesn't work.  is there a way to uninstall and reinstall it, or fix it?

---

### Post by mseney on 2006-12-28
I've also experienced the same issue on Edgy Eft 6.10 which has Serpentine 0.6.91-0ubuntu4. Hopefully this will get fixed!

-------------------------------------Edit--------------------------------------------------------------------------------------------------
[https://bugs.launchpad.net/distros/ubuntu/+source/serpentine/+bug/77655](https://bugs.launchpad.net/distros/ubuntu/+source/serpentine/+bug/77655)

I am using Edgy with Serpentine 0.6.91-0ubuntu and the "Write to Disc" button doesn't work. I have tried re-installing the package, running it with sudo, and nothing works. Finally I found a guide on how to make a .deb package from the source code and so obtained version 0.7-1 from [http://developer.berlios.de/projects/serpentine](http://developer.berlios.de/projects/serpentine) and built the package and installed it. Now the "Write to Disc" button works. Just submitting this bug so it can be fixed automatically by using update manager for the average user.

---

### Post by angelsneverdie on 2007-01-24
I'm still having the same problem - and as far as making a .deb package, that seems a bit over my head -

---

### Post by H.E. Pennypacker on 2007-03-23
angelsneverdie, I do not recommend you try to create your own .deb package.  Instead, this problem can be solved by upgrading to the latest Serpentine version: .07.  You can go through the usual ./configure, make, make install process, or you could wait for a .deb to be uploaded.  I have created an imperfect .deb of the latest version, but I am first checking with the original creator of Serpentine to see if he'll upload it to his website.

If you can't or don't want to wait, I'll send it to you by email.  Just PM me.

---

