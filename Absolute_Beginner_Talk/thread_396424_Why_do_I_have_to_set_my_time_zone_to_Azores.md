---
title: "Why do I have to set my time zone to Azores?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-29
On Edgy ver. 6.10.
I live in mountain time zone USA
Why do I have to set my timezone to the Azores to get the time set correctly??
Probably every body knows about this already.
Thanks

---

### Post by linuxjerk on 2007-03-29
No one has this problem setting their clock?

---

### Post by spinflick on 2007-03-29
Where do you live?

---

### Post by linuxjerk on 2007-03-29
Mountain time USA

---

### Post by oilchangeguy on 2007-03-29
right click on the clock, click adjust time and date, click select time zone.

---

### Post by linuxjerk on 2007-03-29
For some reason after I do that and reboot into windows my time is 4 or so hours behind.
I know, don't reboot into windows. :lolflag:

---

### Post by qamelian on 2007-03-29
> **linuxjerk said:**
> On Edgy ver. 6.10.
I live in mountain time zone USA
Why do I have to set my timezone to the Azores to get the time set correctly??
Probably every body knows about this already.
Thanks

Ubuntu may think the system time is set UTC rather than local time. I think there is a check box in the times settings to correct this.

---

### Post by eljalill on 2007-03-29
You could do
zdump -v /etc/localtime | grep 2007
to see, whether your computer intends on still changing the time at any other date...
and if it does or the output is somehow else wrong, try looking in this thread
[http://www.ubuntuforums.org/showthread.php?t=393258&highlight=daylight](http://www.ubuntuforums.org/showthread.php?t=393258&highlight=daylight)

My clock also had problem. But after setting the server from Amsterdam to Bern (obviously I live in Europe), and synchronising a couple times, everything was fine. Those Swiss sure know how to keep the time. Too bad you don't have them over there in the new world :)

---

### Post by oilchangeguy on 2007-03-29
also make sure in both os's you've checked the box to set the time from internet time servers.

---

### Post by linuxjerk on 2007-03-29
ok, something really screwy is going on here. The UTC box was not checked.
I checked it.
Now I can put it in the correct zone and the clock in the upper right of the screen
reads correctly. But the clock in the setting screen reads 5 hours behind. :confused: 
I think I'm just not going to worry about it. :)

---

### Post by eljalill on 2007-03-29
My guess (!) would be, that rebooting can probably solve this, as rebooting works miracles :) .
But then I am not sure, which "clock in the settings screen" you are talking about.

---

