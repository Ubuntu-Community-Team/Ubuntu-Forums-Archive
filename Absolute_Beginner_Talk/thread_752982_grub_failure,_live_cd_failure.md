---
title: "grub failure, live cd failure"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by noswal on 2008-04-12
About 2 years ago I installed ubuntu partitioned on my hard drive and it worked and got some use out of it. Recently I up graded my pc and now at start up where it has menu option for windows and ubuntu - grub, it does not load ubuntu when I select it, but just hangs.

I then looked up ways to reactivate grub and they refer to using issuing commands from desktop from live cd - But, it goes thru start up process and says cant install x server - no screen found. I have an LG flatron  L2222Ws  

So, how do I get live cd to recognize  that I have a screen

and/or how do i get access to grub to activate it

---

### Post by LaRoza on 2008-04-12
What exactly did you change during this upgrade? Software? Hardware?

---

### Post by noswal on 2008-04-12
Upgraded mobo, graphics card GeForce 8600 Gt, screen LG flatron L2222Ws 2 gig mem etc. Only the hard drives were from other pc.

However, since found other post that directed me to supergrub [http://forjamari.linex.org/frs/?group_id=61&release_id=589](http://forjamari.linex.org/frs/?group_id=61&release_id=589) and installed 
auto_super_grub_disk_1.0.exe  so the grub problem is sorted.


However, now it begins to load ubuntu but hangs on X server not found, and goes to login/password so I can access root but nothing else. I cant to connect to internet so if there is any update I need I cant install.

---

### Post by noswal on 2008-04-12
solved....

After being stuck with a terminal screen and no screen found errors, used this to solve it and now can boot back in to my old unbuntu.
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

so, next will have to think about upgrading from Ubuntu Breezy 5.10

---

