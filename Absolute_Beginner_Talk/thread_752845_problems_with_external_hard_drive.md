---
title: "problems with external hard drive"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by tannenbaum01 on 2008-04-12
Hi!

I have a WD 250 Gig external 2.5 harddrive with USB 2.0 connection and a 3 year old HP pavilion laptop.

I can access and use the external drive as normal - but my problems arise when I use DC++ for example. After every time I disconnect the external drive - this program needs to ree-hash all the files in my share directory.

At first I did not know why this happened but then I realized that it was a problem similar to an old windows XP problem I had years ago. In XP if your external drive is normally for example F:, and you have something else connected as F: when you connect the external drive - it will get another mount point such as G: or something. 

Here's what's happening, when I look in /media, I find these (I guess old mountpoints):
WD Passport
WD Passport_
WD Passport__
WD Passport___ and so on...

I only use this external drive and a music player that I connect.

Anyone who know anything about this problem?

Thanks for the help!

/Christian

---

### Post by Rocket2DMn on 2008-04-12
Are you unmounting the drive before you disconnect it?
You need to right click the icon on the desktop and hit "Unmount" before you unplug the drive.

---

### Post by Kummerpaule on 2008-04-14
same problem here,

how did u solve it and get rid of all the 'fake external hard drives' that are left?

cheers!

---

### Post by jeroen.kurvers on 2008-04-14
Hi, this is a known bug I believe: [https://bugs.launchpad.net/bugs/101845](https://bugs.launchpad.net/bugs/101845)

---

