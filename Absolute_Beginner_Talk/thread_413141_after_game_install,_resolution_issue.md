---
title: "after game install, resolution issue"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by takayuki on 2007-04-18
Hi,

after attempting to install a windows game via crossover, when i quit the game, i'm stuck in a slightly lower resolution than before.

i restarted x using a backed up copy of my xorg.conf file, and i still had the same issue:

i can only get 1152x864, *even though* in my xorg.conf file i've got 1280x1024 listed.  and this is a clean copy of a formerly working xorg.conf file.

when i reboot, at the login screen the resolution is 1280x1024 as it should be, but then just before the desktop loads, i hear a monitor refreshing noise (tick) and the res drops to 1152x864.  

any ideas?


thanks,

takayuki

---

### Post by TURNER on 2007-04-19
Wow...seems like a strange issue!

I've just over come some resolution issues myself, very frustrating.

Although your back up Xorg.conf file did work previously, do you think it might be worth trying to reconfigure the xorg.conf again?

```
sudo dpkg-reconfigure xserver-xorg
```

Second guess.....perhaps the game install f**ked up your graphics card settings? Which Graphics card are you using?

---

