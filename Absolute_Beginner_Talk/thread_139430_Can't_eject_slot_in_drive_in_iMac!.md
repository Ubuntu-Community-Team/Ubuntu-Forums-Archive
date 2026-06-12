---
title: "Can't eject slot in drive in iMac!"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by rephlex on 2006-03-04
Hi! I've just installed ubuntu for ppc and it all went just fine. Only problem I got is that I installed it on an iMac. As most of you already know, the iMac's mouse consist of only one button. Now i've loaded a dvd into the iMac's slot in dvd drive, and now I just don't know hot to eject the dvd out. There are no buttons on the body och de iMac that allows you to just push it and eject the dvd. And i've tried opening various media player software in ubuntu to see if maybe they got an eject button which I could use. But so far no luck. The dvd is stuck in there and I need help. I mean how do you righ klick on an iMac with ubuntu on it, or is there any other way for me to do this?
Please help, I would be forever grateful!
/sweden

---

### Post by Pragmatist on 2006-03-04
I would try the **eject** command```
sudo eject device 
``` put /dev/dvd or whatever your device is called.

The other thing you might consider is mapping your eject key on your MAC keyboard (they do have one right?)

First see if the **eject** command works.

---

### Post by linear on 2006-03-06
Possibilities:

1. There's an eject key at the upper right corner of the Mac keyboard. Supported in Ubuntu.

2. The F12 key is used for a right-click if all you have is a one-button mouse.

3. If all else fails, there should be a small hole at the extreme right of the slot. Insert the end of a small paper clip (gently) to manually eject.

---

### Post by Pragmatist on 2006-03-06
What happened with the eject command?

---

