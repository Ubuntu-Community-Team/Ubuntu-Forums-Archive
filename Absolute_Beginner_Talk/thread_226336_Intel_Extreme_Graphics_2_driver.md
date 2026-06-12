---
title: "Intel Extreme Graphics 2 driver"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-07-31
Hey! I was wondering if anyone knew where I could get a Intel Extreme Graphics 2 driver for Kubuntu/Ubuntu? I have the .exe file but I cant seem to find it for Linux!
Thanks

---

### Post by brnetonboy on 2008-03-14
I need this too. I just installed Ubuntu 7.10 on my Dell Dimension 1100. The video card is onboard, but I think I can get better performance out of it if I use a better driver--I think Ubuntu is just using a default driver right now...

---

### Post by owenman on 2008-06-07
haha yeah! I'm in the same boat.

---

### Post by Tomatz on 2008-06-07
You should be using trhe intel xorg driver by default. If you are not you can enable it like this:

**7.10 users**

In a terminal type:

```
sudo dpkg-reconfigure xserver-xorg
```

follow the prompts and select the **intel** driver.
[B]
8.04 users[/B]

In a terminal type:

```
gksu displayconfig-gtk
```

Select the appropriate driver.

;)

---

