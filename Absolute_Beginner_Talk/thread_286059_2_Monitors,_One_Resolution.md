---
title: "2 Monitors, One Resolution?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by sgardne on 2006-10-27
Hello,

I've done a bit of searching on the forum, but have not found anything straightforward about this. Here's the situation:

I have a laptop (Dell D610) that I use at work and at home. At work, I'd like to use my nice 17" LCD display at it's native resolution (1280x1024) but I can't figure out how to make Ubuntu recognize the fact that there are actually 2 monitors. Both the laptop's display and the external monitor display exactly the same information at the same resolution (1024x768).

How do I tell Ubu to display at one resolution on the laptop's display and another on the external display? 

Thanks!

---

### Post by CatKiller on 2006-10-27
What you've got is your laptop display being **clone**d to the external monitor. You'll need to look at the other threads for the information to establish why, and how to change it.

---

### Post by bodhi.zazen on 2006-10-27
Why look further?

Try these:

Best: [How to laptop dual monitor](http://ozlabs.org/~jk/docs/mergefb/)

Sample xorg.conf: [Sample xorg.conf](http://www.linux-on-laptops.com/forum/showthread.php?p=1253)

Presentations: [Presentations](http://www.astro.umd.edu/~teuben/linux/laptop-display.html)

---

### Post by sgardne on 2006-10-27
> **bodhi.zazen said:**
> Why look further?

Try these:

Best: [How to laptop dual monitor](http://ozlabs.org/~jk/docs/mergefb/)

Sample xorg.conf: [Sample xorg.conf](http://www.linux-on-laptops.com/forum/showthread.php?p=1253)

Presentations: [Presentations](http://www.astro.umd.edu/~teuben/linux/laptop-display.html)

Thank you. The answer does seem to be in that first link, but HOLY COW hard. Dang. I'd like to suggest that this should be something of a priority for upcoming versions of Ubu. Having an easy to use GUI driven configuration interface seems like the way to go. 

Thanks again. I'll see if I can hack it. I'll probably break it, but I'll let you know either way.

-S

---

### Post by bodhi.zazen on 2006-10-27
BACKUP your current xorg.conf !```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

