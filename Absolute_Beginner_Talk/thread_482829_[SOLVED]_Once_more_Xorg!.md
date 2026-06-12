---
title: "[SOLVED] Once more Xorg!"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-24
Hi - I am likely to be reinstalling Ubuntu shortly for various reasons. Amongst them I can't get Amarok to start after an upgrade and I use that all day!

However it took me quite a little while to get my monitor and TV out setup properly and I really don't want to go there again if I can avoid it :)

1 - If I copied my xorg.conf to my other partition which is seperate from Ubuntu would I be able to copy it back to      /etc/X11 once I had the nvidia drivers installed?

2 - Also once I have my sources sorted, and I guess I can save that too, for apt-get am I right in assuming that I can do

```
sudo apt-get install <program> <program> <program> <program> 
``` etc..


thanks for you help :D

---

### Post by swisscow on 2007-06-24
Yes and Yes should be the answers!

Xorg: If you load up all the drivers as before it should work but do a backup before you copy the 'working' xorg over ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bup
```

Sources list should be no problem, just remember to update atfer you have changed the sources ```
sudo apt-get update
```

---

### Post by forestpixie on 2007-06-24
thought as much just wanted another input

thanks

Indeed that was fine, Xorg works.

---

