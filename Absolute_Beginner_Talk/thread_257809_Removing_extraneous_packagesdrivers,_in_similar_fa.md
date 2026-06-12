---
title: "Removing extraneous packages/drivers, in similar fashion to  Windows services"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Zyzzyx on 2006-09-15
Ah, continuing to get comfortable with Ubuntu. Settling in, slowly.

Something I was wondering about was the ability (or necessity?) of removing un-used programs and services. Over the years of using XP it has become fairly standard for me to run down the Services list and Disable, or set to Manual, many of the services that I wouldn't come close to needing, but would likely slow down the system.

Is there something similar to be done in Linux? Can it be done? Does it need to be done?


I thought I could some stuff, but seem to be stymied. Looking through the installed packages, saw something about bluetooth printing (bluez-cups). I don't have anything bluetooth. Don't even have a printer. But when I marked that package for removal was told that that *ubuntu-desktop* would also be removed. YIKES! That didn't sound good, so backed right off. However, found similar odd connections with other stuff.

---

### Post by Najand on 2006-09-15
"ubuntu-desktop" is a complex of different packages. Soowhen you try to remove of the packages included, it will ask that the complex (not any ot other packages included) will be removed. It does not have any effect to your system if you remove "ubuntu-desktop". I removed it quite a few months ago  when I removed "bittorrent" package and nothing went wrong to my system.

---

### Post by aysiu on 2006-09-15
You can remove *ubuntu-desktop*. It's just a pointer to all the default packages in Ubuntu.

Also, if you install *bum*, you can use it to disable services you don't need.

---

### Post by Zyzzyx on 2006-09-15
Ah, good information, both. Thanks.

I did go ahead and remove the *bluez-cups*, and while it complained about breaking *ubuntu-desktop*, you're right, everything still seems fine.

And that *bum* is an interesting one. Runlevels. I can see that's something else I'll want to learn about. And take a peek at how to change them from terminal, without the GUI. Would like to learn that way, and then use GUI tools if they're faster/easier.

---

