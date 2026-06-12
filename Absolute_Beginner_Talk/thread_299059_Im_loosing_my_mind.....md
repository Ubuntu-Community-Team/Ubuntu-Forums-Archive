---
title: "Im loosing my mind...."
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by egelston on 2006-11-13
I just installed UBUNTU and everything seems fine...except for the internet. Clicking and dragging windows takes at least 2 seconds. When i scroll up or down a page a "ripple" effect happens and takes seconds to complete. Any help?!?](*,)

---

### Post by taurus on 2006-11-13
Sounds like you need to install a driver for your graphic card?  What kind of graphic card do you have anyway?

---

### Post by egelston on 2006-11-13
it says powercolor tul theater 550 pro tuner by Nvidia...i have everything running fine...this has been my only problem...

---

### Post by egelston on 2006-11-13
wow im smart...fixed the problem...should have read more into the forum. thanks though!

---

### Post by djaya2 on 2007-01-09
> **egelston said:**
> it says powercolor tul theater 550 pro tuner by Nvidia...i have everything running fine...this has been my only problem...

How did you solve the problem?  I thought the Theater 550 Pro chip doesn't work with Linux.  Are you able to use it as a tuner?

---

### Post by Ben Sprinkle on 2007-01-09
5th time posting this:
```

sudo dpkg-reconfigure xserver-xorg

```
Pick your ddriver and reboot.

---

