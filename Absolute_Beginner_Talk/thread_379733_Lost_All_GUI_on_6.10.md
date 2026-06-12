---
title: "Lost All GUI on 6.10"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by wanttoknow on 2007-03-08
I installed xrandr and then removed it, I rebooted and there is no GUI at all. I apt-get installed x11-common, GDM, and a couple others. Now when I start the computer up I get the GUI loaded but just the background loaded, and nothing else.

There is no login prompt or anything, just a mouse pointer and a gold background, and thats it. 

Please help!!!

---

### Post by Daishiman on 2007-03-08
Reinstall the gdm package, which is the desktop manager, which should install all the other packages properly.

If that doesn't work, reinstall with sudo aptitude install the ubuntu-desktop package.

---

### Post by wanttoknow on 2007-03-09
Thanks a bunch I will try installing the ubuntu desktop and see where that leaves me. I was about to wipe it all too. 

Thanks

---

