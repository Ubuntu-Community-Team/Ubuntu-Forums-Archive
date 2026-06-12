---
title: "How to change the clock &amp; display resolution"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by renesisspeed on 2006-09-04
Just got xubuntu 6.06 up and running and have two problems.

1. I have it installed on and old laptop with a fairly small screen, and it only gives me the option of setting the resolution to "Default" and 320x240(which is just way too big)
Even with the default setting many of the dialoug boxes are too large to fit in the display area, so I have to drag the window around to be able to see the buttons etc.

2. The time is not set properly and I cant find how to change it, I right click on the clock and it wont let me click "Clock". (I'm sure this is probably very simple but i'm clueless):-)

Thx in advance
 - renesisspeed

---

### Post by dbasis on 2006-09-04
i had an similar problem, thought the highest resolution, had still too big winows, etc. - i went to the settings menu and there must be something like "fonts" or so, if u than click on "details" u can change the resolution. That gave me the feeling of having a higher resolution.

---

### Post by renesisspeed on 2006-09-04
well, that helps a little, but They still hang out of the display area :-(

---

### Post by renesisspeed on 2006-09-07
I still havent found out how to set the clock...:-# so...BUMP...

but got the display problem solved in another post with a user with the same problem :-)
[http://www.ubuntuforums.org/showthread.php?p=1475114#post1475114](http://www.ubuntuforums.org/showthread.php?p=1475114#post1475114)

---

### Post by CatKiller on 2006-09-08
> **renesisspeed said:**
> I still havent found out how to set the clock...:-# so...BUMP...

Applications -> System -> Time and Date

I find Xubuntu quite confusing with the Settings, System and Settings Manager bits all doing similar things.

---

### Post by bodhi.zazen on 2006-09-08
> **renesisspeed said:**
> I still havent found out how to set the clock...:-# so...BUMP...

but got the display problem solved in another post with a user with the same problem :-)
[http://www.ubuntuforums.org/showthread.php?p=1475114#post1475114](http://www.ubuntuforums.org/showthread.php?p=1475114#post1475114)

What do you want to set? Time, timezone, look & flle?

Timezone - tzconfig -> choose time zone.
```
sudo tzconfig
```

Time - I use ntpdate and ntpd

```
ntpdate ntp.nasa.gov
```

After seting the date you can run ntpd to keep in sync with a time server.

---

