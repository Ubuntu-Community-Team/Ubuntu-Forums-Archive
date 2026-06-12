---
title: "Absolute NOOB--Screen resolutions---"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by ejizzel on 2008-04-18
extreme linux virgin over here, I first wanted to say hello first. I used the LIVE CD for 8.04  and decided to do a install, I noticed that the screen resoltions available on the live cd are unavailable when installed. did I do something wrong. Im trying to get the screen to 1024X768

---

### Post by zvacet on 2008-04-18
Applications>accessories<terminal

```
sudo dpkg-reconfigure xserver-xorg
```

That way you will be able to choose ersolution you want to use.if after reboot you still have low rresolution go to the system>preferences>screen resolution and fix it there.

---

