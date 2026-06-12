---
title: "keyboard lags when typing fast"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2007-05-19
My problem is exactly what it sounds like. I can't figure out why but for some reason when I type the keyboard just has terrible lag. then, it will catch up to what I am doing all at once. Any ideas?

---

### Post by mongooseman1128 on 2007-05-19
I also just noticed that when I hit backspace in mozilla it doesn't take me to the previous page. ever.

---

### Post by r3bol on 2007-05-19
I've noticed this problem when I've been running various OS on a low spec machines. What machine are you running on?

---

### Post by jordanmthomas on 2007-05-19
To fix your firefox issue:
from [https://answers.launchpad.net/ubuntu/+source/firefox/+question/3578](https://answers.launchpad.net/ubuntu/+source/firefox/+question/3578)

> In the location bar, open the URL "about:config". In the "Filter" section, type "backspace". Below that, you will see "browser.backspace_action". Double-click on that line, and a popup window will appear. Just type in "0" (zero), and click "OK". After that, your Backspace should be the way you want it. :)

Not sure about your other issue, but hey...something's better than nothing, right?

---

### Post by mongooseman1128 on 2007-05-19
This is being run on a brand new HP dv6308nr. I have 2 GB RAM and a AMD turion 64 X2 (clocked at 1.6). I checked my averages and I'm only using 17% of my processor power

---

### Post by mongooseman1128 on 2007-05-19
thanks so much jordan I did that and now I have my beloved backspace back

---

### Post by r3bol on 2007-05-20
Could it be that mongooseman1128 has too much RAM? That is info randomly stored there is taking longer to be accessed because there is more places for the machine to look. I know this sounds crazy, but its something  a friend was talking about last week to me. 
If this makes any sense mongooseman1128, you could try ant take out a gig and see if it helps.

---

### Post by mongooseman1128 on 2007-05-20
Thanks for the suggestion r3bol, but it didn't do the trick. I think what your friend is forgetting is that the system will only fill as much RAM is it needs to. If my system were to get to the point where it needs all 2 gigs of RAM that would still be faster than if I had 1 gig because than that extra gig that it was needing would be stored on my swap which is far slower than RAM.

---

### Post by mongooseman1128 on 2007-05-20
do I possibly need to get some chipset drivers?

---

### Post by mongooseman1128 on 2007-05-21
are there chipset drivers for linux?

---

### Post by mongooseman1128 on 2007-05-23
hate to do it, but... bump

---

