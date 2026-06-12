---
title: "mac mini sound problem"
date: 2007-06-08
forum: Apple PPC Users
---

### Post by wvmac on 2007-06-08
Ubuntu on my ppc mac mini works great. My apple keyboard controls the volume and the monitor goes to sleep when it is supposed to. However when running kubuntu the volume keys do not work as they are supposed to and the monitor  will not go to sleep.  The screen saver will activate but it will not  power off or go into standby.  I have installed from ubuntu and kubuntu iso's.  When I install ubuntu-desktop to a kubuntu install everything works in ubuntu (gnome). But kubuntu (kde) doesn't operate correctly either way I install it. 
In xorg.conf dpms is present. 
I guess I could post this at the kubuntu site but I like this  forum better since it has a ppc section.
thanks for any help you can give.

---

### Post by luckyd on 2007-06-10
Is it that the options for standby and sleep are not present or is it that when you click them it dosn't work?
I had a problem were the options wouldn't appear, so I ran > sudo dpkg-reconfigure gdm and then I set kdm as the default. Hope that helps...

---

