---
title: "Broadcomm trouble with MacBook Pro 5,1"
date: 2009-06-25
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2009-06-25
Have just installed Jaunty on my shining new MacBook Pro 5,1.
I have by now, after a number of installations, a certain routine, so I install ubuntu-tweak, wicd and reboot.
Much to my surprise, the WiFi begins to connect and disconnect, repeating this cycle and becoming essentially useless.
I see that it is using a proprietary driver and, under Mac OS, the WiFi card is indicated as Broadcomm BCM43xx 1.0 (5.10.38.35).
From a couple of threads I have read I haven't understood where is the problem and how to solve it - only cryptic remarks on backports etc.
Would any of the good folks who understand these cards advice me, in intelligible terms, on what to do please?
Thank you.

---

### Post by alexmurray on 2009-06-25
Why are you using wicd? My MBP 5,1 works perfectly fine with NetworkManager (no drop outs etc) and its using the wl driver which was installed and activated by default - I didn't have to do anything.

---

### Post by GeneralSunTzu on 2009-06-25
> **alexmurray said:**
> Why are you using wicd? My MBP 5,1 works perfectly fine with NetworkManager (no drop outs etc) and its using the wl driver which was installed and activated by default - I didn't have to do anything.

Old habit, I guess.
On my previous MacBook Pro it was far superior to Network Manager.
Will give it a try to get rid of Wicd and see whether I can make it work with Network Manager.

Thanks for the advice.

---

### Post by GeneralSunTzu on 2009-07-03
So back I went to the gnome Network Manager and indeed it works.
This must be the first time it works the other way around.
Perhaps I shoud tell the wicd people...
Thanks Alex: by JJ Network manager has overtaken wicd...

---

