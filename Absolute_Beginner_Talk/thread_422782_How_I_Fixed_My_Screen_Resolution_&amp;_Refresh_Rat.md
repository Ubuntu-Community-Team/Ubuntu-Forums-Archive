---
title: "How I Fixed My Screen Resolution &amp; Refresh Rate!"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by maynoth on 2007-04-25
Hello,

For those of you pulling your hair out with editing xorg.conf and not having the settings work in feisty, here is how I fixed it.

1. Find out your max display size and refresh rate in windows.
Mine is 1280x1024 75hz

2. Plug those numbers into this 
[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)
this will show you your vertical and horizontal refreshrate

3. sudo dpkg-reconfigure xserver-xorg

run through this (i used defaults),  when you get to the part about screen size de-select all options (space bar) that you don't need, and select (space bar) the one you do.

enter you refresh rates..  mine was 80.42 for horizontal and 75.00 for vertical

---

### Post by RedSquirrel on 2007-04-25
This guide is also very helpful:

[ HOWTO change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?p=454217")

---

### Post by phr0ze on 2007-04-25
The site didn't list my resolution, so I used a close match, then I modified the URL to use my resolution.

```
Before:
http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1024+768&FREQ=60

After:
http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1280+768&FREQ=60
```

Worked fine.

Thanks.

---

### Post by u.b.u.n.t.u on 2007-04-25
Another method is waiting for Gutsy Gibbon when this issue will hopefully have been resolved.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731)

It has been a known problem since at least October 2005.

Finally something will hopefully be done about it.

The status of this problem has been confirmed, it is maked as critical and the highly talented Ubuntu X SWAT have been assigned to it.

So with a bit of luck, editing the xorg.conf will be a thing of the past in the not too distant future.

:grin:

---

### Post by maynoth on 2007-04-30
I hear Xorg 7.3 wont have the xorg.conf...  THANK GOD!  I just hope it will have tool to override detected refresh rates and resolutions, because it didn't let me have my max res or refresh by default..

---

### Post by gomets11 on 2007-05-01
i had this problem too...i tried every which way to fix it...finally i just went with a fresh install and it solved the problem..i then installed the nv restricted driver and had the problem again...i uninstalled it and now i'm back to my normal screen res...i guess the driver has an issue

---

